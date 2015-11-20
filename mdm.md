# Master Data Management

* Present Master Data in a contentual and constent manner

* Single version of truth

* Relationships between various master records. eg. influncers, hierarchies, households

* Events related to the records - Life events, merges, splits

* Why
	* Governace and Compliance
	* Consitent Customer Information
	* Eliminate Duplicate Data
	* Provide a 360 degree view of the customer
	* Tracebility
	* Accurate Reporting

* Patterns of Integration
	* Sync UI Integration - Custom link to MDM to administer data which then sends data back to Salesforce
	* Sync Web Services Integration - Visualforce page which calls seach API and then triggers updates back
	* Async Web Service - Record update in Salesforce triggers a process in MDM to identify and create a record
	* Async Batch Integration - Daily changes synchronized

* How
	* Analytical MDM - Leveraged by the BI team. Data is augmented by insights. Created async.
	* Referential - Hub contains linkage which are created async. Data resides in each system.
	* Operational - All applications directly create data in MDM.

* Implementional Approaches
	* Registry Hub - Light weight, easy to build, governance is a challenge
	* Transactional Hub - Has core attributes, long implementation cycle, single version of truth, Data Governance and Stewardship is built in.
	* Hybrid - In between the two (point in time)
	* Cloud based MDM eg. Data.com, Unified front end, Social Stewardship

* Data Stewardship
	* Process should be easy
	* Automate process through rules
	* Leverage Chatter, approval process etc
	* Mistake proof application for better data capture

* MDM and CRM complement each other. CRM enables MDM to create better master data. MDM provides better visibility to CRM related data.



