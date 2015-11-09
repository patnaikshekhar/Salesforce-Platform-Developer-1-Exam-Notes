# Exception Handling

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
 	* getCause: Returns the cause of the exception as an exception object.
	* getLineNumber: Returns the line number from where the exception was thrown.
	* getMessage: Returns the error message that displays for the user.
	* getStackTraceString: Returns the stack trace as a string.
	* getTypeName: Returns the type of exception, such as DmlException, ListException, MathException, and so on.
	* Some exceptions such as DML exceptions have special methods
		* getDmlFieldNames - Returns the names of the fields that caused the error for the specified failed record.
		* getDmlId: Returns the ID of the failed record that caused the error for the specified failed record.
		* getDmlMessage: Returns the error message for the specified failed record.
		* getNumDml: Returns the number of failed records.
 
 * Famous DML Exceptions
 	* **DmlException** - Problems with DML Statements
 	* **ListException** - Any problem with a list such as index out of bounds exceptions
 	* **NullPointerException** - Problems with dereferencing a null variable.
 	* **QueryException** - Any problem with SOQL queries, such as assigning a query that returns no records or more than one record to a singleton sObject variable.
 	* **SObjectException** - Any problem with sObject records, such as attempting to change a field in an update statement that can only be changed during insert.

* To create a custom exception use
```java
	public class MyException extends Exception {}
    
    // To create an exception
    new MyException();
    
    new MyException('This is bad'); // Error Message input
    
    new MyException(e); // Exception argument
    
    new MyException('This is bad', e); 
    // The first is the message and the second is the cause.
```