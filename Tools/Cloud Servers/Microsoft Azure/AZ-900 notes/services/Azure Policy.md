A service to create, assign, & manage policies that control / audit resources.

How define:
- can define both individual policies & initiatives (groups of related policies)
- evaluates resources to see which ones aren't compliant with created policies + prevent noncompliant resources from being made
- can be set at any level + can be inherited 
- comes with built-in policy & initiative definitions for [[Azure Storage]], Networking, Compute, Security Centre, Monitoring
- can sometimes remediate non compliant resources & configs to ensure integrity of resource state
	- can also flag resources as exception to prevent those resources from being automatically fixed
- integrates with [[Azure DevOps]] thru [[continuous integration]] & delivery pipeline policies

Initiatives:
- initiative definition contains all policy definitions to track compliance state
- Enable Monitoring initiative policy definitions:
	- monitor unencrypted SQL Database in Security Centre
	- monitor OS vulnerabilities in Security Centre
	- Monitor missing Endpoint Protection in Security Centre
	- there's like 100 more

