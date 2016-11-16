# Async Apex

## Scheduable

 * Used to run apex code at specific times
 * Uses the **Scheduable** interface which requires that the execute function be implemented
 * Example:

 ```java
 global class MySchedulableClass implements Schedulable {
 	global void execute(SchedulableContext ctx) {
    	CronTrigger ct = [SELECT Id, CronExpression, TimesTriggered, NextFireTime FROM CronTrigger WHERE Id = :ctx.getTriggerId()];
      	System.debug(ct.CronExpression);
      	System.debug(ct.TimesTriggered);
    }
 }
 ```

 * Use **System.schedule** to schedule a job. Format
 ```java
 // For Midnight on march 15
 // Format is
 // Seconds Minutes Hours Day_of_month Month Day_of_week optional_year
 public static String CRON_EXP = '0 0 0 15 3 ? 2022';
 
 System.schedule(NameOfJob, CRON_EXP, new MySchedulableClass());
 ```
 * When Test.StartTest() is used then the job run immediately instead of waiting for Cron time.
 * You can only have **100** classes scheduled at one time.
 * The Scheduled Jobs setup item can be used to find currently scheduled jobs

## Apex Batch Processing

* Lets you process batches asynchronously
* Each invocation of a batch class results in a job being placed on the Apex job queue for execution.
* The execution logic is called once per batch
* **Default batch size is 200**, you can also specify a custom batch size.
* Each new batch leads to a new set of Governor limits
* Each batch is a descrete transaction
* A batch class has to implement the **Database.Batchable<sObject>** interface
* Example:

```java
global class CleanUpRecords implements Database.Batchable<sObject> {
	
    global final String query;
    
    global CleanUpRecords(String q) {
       query = q;
	}
    
	// The start method is called at the beginning of a batch Apex job. It collects the records or objects to be passed to the interface method execute.
	global Database.QueryLocator start(Database.BatchableContext BC) {
    	return Database.getQueryLocator(query);
    }
    
    // The execute method is called for each batch of records passed to the method. Use this method to do all required processing for each chunk of data.
	global void execute(Database.BatchableContext BC, List<sObject> scope){
      delete scope;
      Database.emptyRecycleBin(scope);
    }
    
    // The finish method is called after all batches are processed. Use this method to send confirmation emails or execute post-processing operations.
    global void finish(Database.BatchableContext BC){
           AsyncApexJob a =
               [SELECT Id, Status, NumberOfErrors, JobItemsProcessed,
                TotalJobItems, CreatedBy.Email
                FROM AsyncApexJob WHERE Id =
                :BC.getJobId()];
           // Send an email to the Apex job's submitter
           //   notifying of job completion.
           Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
           String[] toAddresses = new String[] {a.CreatedBy.Email};
           mail.setToAddresses(toAddresses);
           mail.setSubject('Record Clean Up Status: ' + a.Status);
           mail.setPlainTextBody
           ('The batch Apex job processed ' + a.TotalJobItems +
           ' batches with '+ a.NumberOfErrors + ' failures.');
           Messaging.sendEmail(new Messaging.SingleEmailMessage[] { mail });
    }
}
```
* Batches of records are not guaranteed to execute in the order they are received from the start method.
* The maximum number of records that can be returned in the
Database.QueryLocator object is **50 million**.
* Test methods can execute only one batch.
* To execute a batch job use **Database.executeBatch**
```java
CleanUpRecords c = new CleanUpRecords(query);
Database.executeBatch(c);
```
* Batches can be scheduled using a scheduler class
