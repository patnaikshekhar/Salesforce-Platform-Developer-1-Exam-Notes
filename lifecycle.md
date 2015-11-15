# Development Lifecycle

* Typical Development Lifecycle for Developing in Production
	* Plan functional requirements.
 	* Develop using Salesforce Web tools, using profiles to hide your changes until they’re ready to deploy.
 	* Update profiles to reveal your changes to the appropriate users.
 	* Notify end users of changes.

* Typical Development Lifecycle for Developing in a Sandbox
	* Create a development environment. 
	* Develop using Salesforce Web and local tools.
 	* Test within the development environment.
 	* Replicate production changes in the development environment.
 	* Deploy what you’ve developed to your production organization.
 	
* Ways of migrating changes between Sandboxes and Production
	* Change Sets
	* ANT Migration Toolkit
	* Force.com IDE

* Typical Development Cycle for developing in Dev and Test
	* Create a development environment.
	* Develop using Salesforce Web and local tools.
	* Create a testing environment.
	* Migrate changes from development environment to testing environment.
	* Test.
	* Replicate production changes in other environments.
	* Deploy what you’ve developed to your production organization.

* Developing Multiple Projects with Integration, Testing, and Staging
  * Create development environments.
  * Develop using Salesforce Web and local tools.
  * Create testing environments, including UAT and integration.
  * Migrate changes from development environment to integration environment.
  * Test.
  * Migrate changes from integration environment to UAT environment.
  * Perform user-acceptance tests.
  * Migrate changes from UAT environment to staging environment.
  * Replicate production changes in staging environment.
  * Schedule the release.

* Types of Sandboxes
	* Developer - Developer sandboxes copy customization (metadata), but don't copy production data, into a separate environment for coding and testing.
	* Developer Pro - Developer Pro sandboxes copy customization (metadata), but don't copy production data, into a separate environment for coding and testing. Developer Pro has more storage than a Developer sandbox. It includes a number of Developer sandboxes, depending on the edition of your production organization.
	* Partial Copy - A Partial Copy sandbox is a Developer sandbox plus the data that you define in a sandbox template.
	* Full Copy - Full sandboxes copy your entire production organization and all its data, including standard and custom object records, documents, and attachments. Use the sandbox to code and test changes, and to train your team about the changes. You can refresh a Full sandbox every 29 days.

* Uses of Sandboxes
	* Developer - Developer or Developer Pro sandbox
	* Testing - Unit tests and Apex tests: Developer or Developer Pro sandbox, Feature tests and regression tests: Partial Copy sandbox (with a standard data set loaded)
	* Testing external integrations - Full sandbox is best when an external system expects full production data to be present. Partial Copy sandboxes may be appropriate in special cases when you want to use sample data or a subset of your actual data. Works well if you’re using external IDs.
	* Staging and user-acceptance testing - Full sandbox is best for validation of new applications against production configuration and data. Partial Copy sandboxes are appropriate if testing against a subset of production data is acceptable, for example, for regional tests.
	* Production debugging - Full Copy Sandbox

* Use Web-based importing when:
  * You are loading less than 50,000 records.
  * The object you need to import is supported by import wizards. To see what import wizards are available and thus what objects they support, from Setup, enter Data Management in the Quick Find box, then select Data Management.
  * You want to prevent duplicates by uploading records according to account name and site, contact email address, or lead email address.

* Use Data Loader when
	* You need to load 50,000 to 5,000,000 records. Data Loader is supported for loads of up to 5 million records. 
	* You need to load into an object that is not yet supported by the import wizards.
	* You want to schedule regular data loads, such as nightly imports.
	* You want to export your data for backup purposes.

* Process of Developing Applications in a Release Train
	* Plan your release around Salesforce upgrades.
	* Schedule your concurrent development projects. This will help you determine if the new functionality can be done now, in the current release, or sometime in the future.
	* Establish a process for changes to the production organization.
	* Track changes in all environments. This will ensure that short-term functionality that is delivered to production does not get overwritten
when you deploy from your development environment.
	* Integrate changes and deploy to staging or test environments.
	* Release to production.

* 