# Testing

* Minimum **75%** test coverage required to deploy to production
* All tests must **pass** in order to deploy to production
* **@isTest** annotation is put on the class to indicate that it is a test class
* The test classes don't count towards the 3MB org code size limit
* Test methods need to be static and are defined using the testmethod keyword or with the @isTest annotation

```java
static testmethod void myTest() {
    // Add test logic
}
```

or 

```java
static @isTest void myTest() {
    // Add test logic
}
```

* The tests can have only one Test.startTest() and Test.stopTest() block. This block ensures that other setup code in your test doesn’t share the same limits and enables you to test the governor limits.
