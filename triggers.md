# Triggers

* Standard Trigger Syntax

```java
trigger TriggerName on ObjectName (trigger_events) { code_block
}
```
* The following are the trigger events
	* before insert 
	* before update 
	* before delete 
	* after insert
	* after update
	* after delete
	* after undelete

* Use **addError(errorMessage)** on the Trigger object lists to add an error

