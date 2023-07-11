A hosting service for [[Domain Name System|DNS]] domains providing name resolution thru Azure infrastructure. DNS records can be managed using the same credentials and details as other Azure services.

Benefits:
- reliability & performance - uses anycast networking so each DNS query is answered by closest available DNS server
- security - based on [[Azure Resource Manager]] and uses features like:
	- [[Azure role-based access control]] (Azure RBAC) - controls user access to specific actions in an organisation
	- activity logs - monitors modifications to a resource or troubleshoots errors
	- resource locking - locks subscriptions / resource group / resource to prevent modification or deletion of critical resources
- ease of use - can manage domains & records with Azure portal, PowerShell cmdlets, and Azure CLI
	- apps that need automated DNS management can integrate thru REST API & SDKs
- customisable [[Azure virtual networks]] with private domains - 
- alias records - record sets can refer to an [[Azure resource]] / Content Delivery Network (CDN) endpoint
	- if IP address of resource changes, alias record set updates itself during DNS resolution
	- points to service instance, which is associated with an IP address

Note:
- Azure DNS can't be used to buy a domain name -> must use App Service domains or third-party domain name registrar

