# Salesforce - Platform Developer 1 Certification Notes

These are a bunch of notes that I'm creating while preparing for the exam

 * Standard exception handling syntax - Order from Specific to Generic
 
 ```java
 try {
 } catch(DmlException e) {
 	// DmlException handling code here.
 } catch(Exception e) {
 	// Generic exception handling code here.
 } finally {
 	// Final code goes here
 }
 ```
 
 * Common Exception methods
 	* e.getMessage() - gets the message of the error
 	* getCause: Returns the cause of the exception as an exception object.
	* getLineNumber: Returns the line number from where the exception was thrown.
	* getMessage: Returns the error message that displays for the user.
	* getStackTraceString: Returns the stack trace as a string.
	* getTypeName: Returns the type of exception, such as DmlException, ListException, MathException, and so on.
	* Some exceptions such as DML exceptions
 
 * Famous DML Exceptions
 	* **DmlException** - Problems with DML Statements
 	* **ListException** - Any problem with a list such as index out of bounds exceptions
 	* **NullPointerException** - Problems with dereferencing a null variable.
 	* **QueryException** - Any problem with SOQL queries, such as assigning a query that returns no records or more than one record to a singleton sObject variable.
 	* **SObjectException** - Any problem with sObject records, such as attempting to change a field in an update statement that can only be changed during insert.