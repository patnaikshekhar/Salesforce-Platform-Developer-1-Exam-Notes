# Large Data Volumes

* Force.com query optimizer 
	* Determines the best index from which to drive the query, if possible, based on filters in the query
	* Determines the best table to drive the query from if no good index is available
	* Determines how to order the remaining tables to minimize cost
	* Injects custom foreign key value tables as needed to create efficient join paths
	* Influences the execution plan for the remaining joins, including sharing joins, to minimize database input/output (I/O)
	* Updates statistics

* Skinny Tables - 
	* These are copies of the data for a table with limited number of fields (100 columns). 
	* Are kept in sync with the source data
	* Help in fast data access.
	* Can only contain field from the base object
	* Need to be enabled by support

* Indexes
	* Custom indexes can be created to optimize performance
	* Some indexes such as RecordTypeId, Division, CreatedDate, Name, Email are created by default
	* Indexes for External Id are created by default
	* By default nulls are not considered in the index
	* If a where clause narrows down the crietria to 30% for Standard fields or 10% for Custom fields the index is used
	* Formula fields which are deterministic are indexed
	* A formula field is deterministic if
 		* It does not use TODAY(), NOW(), etc
 		* Does not refer to a different object
 		* Does not refer to a formula field which references a different object
 		* Owner field
 		* Standard field with special functionalities
 	* Two column indexes can also be created for supporting search + sort. These are more efficient than 2 indexes.

* Divisions can be used to partition huge volumes of data by business unit

* Mashups can be used to get real time data from an external system by either using Canvas or Callouts

* Sharing Calculation can be deferred by an admin to speed up data load

* Hard Deletes can be used to optimize performance so that data does not go to the recycle bin.

* Best Practices for Reporting
	* Partition data
	* Minimize no of joins (No of objects and relationships on the report)
	* Reduce amount of data returned - reduce no of fields
	* Use filters which use standard or custom indexes
	* Archive unused records

* Best Practices for Loading Data through API
	* Use the bulk api if you have more than 100,000 records
	* insert() is the fastest followed bu update() and then upsert()
	* Data should be clean before processing. Error in batches cause the records to be processed row by row.
	* Load only changed data
	* For Custom integrations - use http keep-alive, use gzip compression, authenticate only once
	* Avoid switching on sharing during the load
	* Disable Computations such as Apex Triggers, Workflows, etc
	* Group records by ParentId to avoid locking conflicts

* Best Practices for Extracting data from the API
	* getUpdated() and getDeleted() should be used
	* Where more than 1 million records are returned use the Bulk API

* Best Practices for Searching
	* Avoid Wildcards
	* Reduce the no of joins
	* Partition data with Divisions

* Best Practices for SOQL and SOSL
	* Search on Indexed fields
	* Avoid quering formula fields
	* Don't use nulls in where clause

* General Best Practices
	* Consider using an Aggregate Data custom object which is populated using batch apex
	* Consider using a different value instead of null such as N/A
	* Enable Separate Loading of Related Lists setting to reduce the time taken to reduce related list rendering
	* Remove the API User from the sharing hierarchy
	* Consider using a query which reduces the data set to either 30% or 10%
	* Keep the recycle bin empty
	