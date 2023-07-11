Azure ExpressRoute is a private connection to extend an on-premise network to Microsoft cloud services like 365 and Azure. Each location has its own ExpressRoute circuit. Connectivity can be from any-to-any (IP VPN) network, point-to-point Ethernet, or virtual cross-connection thru provider at colocation facility.

Benefits:
- connectivity to Microsoft cloud services across all [[Azure regions]] in geopolitical region
- global connectivity to services across all regions with ExpressRoute Global Reach
- dynamic routing between network & Microsoft via Border Gateway Protocol
- built-in redundancy in every peering location -> higher reliability

Direct access to following services in all regions:
- Office 365
- Dynamics 365
- Azure compute services like [[Azure Virtual Machines]]
- Azure cloud services like [[Azure Cosmos DB]] & [[Azure Storage]]

ExpressRoute Global Reach:
- exchanges data across on-premise sites in different regions thru ExpressRoute circuits without transferring over public internet

Border Gateway Protocol:
- exchange routes btwn on-premise networks & resources running in Azure

Built-in redundancy:
- each provider uses redundant devices for high availability
- can configure multiple circuits to complement

Connectivity models:
- CloudExchange co-location - user's datacenter, office, etc. is physically located at a cloud exchange (e.g. ISP), allowing them to request virtual cross-connect to Microsoft Cloud
- Point-to-point Ethernet connection
- Any-to-any connection - WAN integrates with Azure by providing office and datacenter connections
- direct from ExpressRoute sites - connect directly into global network at peering location, providing dual 100Gbps / 10-Gbps connectivity and Active/Active connectivity support


