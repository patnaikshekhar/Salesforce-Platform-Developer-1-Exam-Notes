# Single Sign On

* Preferred method is Standards based SAML
* Best way is to use the My Domain Feature
* Supports mutiple identity providers
* IDP Sends single sign on messages
* A Service Provider (SP) recieves Single Sign On messages
* Trust is stablished by exchanging meta data
* Messages are digitaly signed XML documents
* Single Sign on works on mobile and desktop app as well when using OAuth
* Issuer is a unique string in the SAML
* IDP Certificate is used to validate the signed request
* Three subjects are supported
	* Salesforce.com username
	* Federation Id
	* User Id from User object
* IDP must support relay state for SP initiated SAML
* Just in time provisioning allows the IDP to create a user in Salesforce, requires to pass provisioning attributes
* Single Sign On is possible for Communities and Portal
* Firefox has a SAML Tracer plugin to debug or the SAML Assertion validator

# Salesforce Identity

* Use connected apps to connect to external apps
* 

# Social Sign On

* Login and OAuth access from public sources
* Use from My Domains features
* Supported Providers
	* Salesforce
	* Facebook
	* Open Id Connect
	* Janrain
* Registration handler class is used to create, update or link to existing users