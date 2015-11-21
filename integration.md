# Integration

* The following are useful tips when coming up with a end state architecture
	* The integration architecture should align with the business strategy
	* Integration architecture should support a mix of batch and real-time
	* Architecture should be based around busines service level agreements (BSLAs)
	* Integration architecture should have clearly defined standard for implementing different use cases

* Typical methods
	* Cloud to Ground (Salesforce.com originated)
		1. The message is relayed to a DMZ end point (either a firewall, reverse proxy or gateway appliance). This is where security authentication occurs. Whitelist IPs, two way SSL, basic HTTP Authentication
		2. DMZ relays the message to the On Premise infrastructure usually an ESB
		3. ESB then may push the message to the SOA infrastructure, source system, Database or EDW etc
	* Ground to Cloud
		1. Most designs use an ESB to connect to Salesforce which provides session management
		2. ETL solutions can be leveraged to send large data volumes
		3. Offline data replication is another scenario
		4. ETL can pull data from Salesforce
	* Cloud to Cloud
		1. Salesforce2Salesforce can be used to connect to other instances
		2. Stay away from building complex integration, instead use a IPaas solution.
		3. Having to build durable and resilient integration solutions inside of Salesforce can be expensive and very complicated
	