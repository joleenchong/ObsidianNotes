The deployment & management service for Azure. It provides a management layer for creating, updating & deleting [[Azure resource]]s in an Azure account.

ARM receives requests from users sent through Azure tools, APIs or SDKs, and authorises & authenticates the request. The request is sent to the Azure service to take the requested action.

Benefits:
- infrastructure managed thru declarative templates, not scripts
- can deploy, manage, monitor resources as a group vs individually
- resource redeployment consistent
- define dependencies btwn resources to order deployment correctly
- [[Azure role-based access control]] natively integrated into management platform -> can apply access control to all services
- apply [[Azure resource tags]] for logical organisation
	- clarify org's billing by viewing costs for group of resources under same tag

ARM templates:
- concept of infrastructure as code - infrastructure managed as lines of code
- a template is a JSON file defining what to deploy to Azure
- deployment code is verified before any code is run -> resources are created & connected correctly
- resources are created in parallel
- Benefits:
	- declarative syntax - create & deploy Azure infrastructure declaratively -> no need to write actual programming commands & sequence to deploy resources
	- repeatable results
	- orchestration - no need to worry abt ordering operations
	- modular files - templates can be broken into smaller components to link at deployment time
		- can nest 1 template inside another
	- extensibility - can add PowerShell / Bash scripts to templates
