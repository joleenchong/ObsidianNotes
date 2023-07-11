Enables Azure resources to communicate with each other, internet users, and on-premise client computers.

Networking capabilities:
- **isolation & segmentation** - can create multiple isolated virtual networks and segment them into subnets
- **internet communications** - assign public IP address to Azure resource or put resource behind public load balancer to receive incoming connections from internet
- **communicate with Azure & on-premise resources**
	- Azure resources - either through virtual network connection or service endpoints
	- On-premise:
		- point-to-site - from client outside of org to corporate network
		- site-to-site - on-premise VPN device / gateway to Azure VPN gateway over internet.
		- [[Azure ExpressRoute]] - dedicated private connectivity to Azure without internet travel -> for greater bandwidth & higher security
- **route & filter network traffic**
	- route tables can define rules on traffic direction and control how packets are routed between subnets
	- Border Gateway Protocol (BGP) - propagates on-premise BGP routes to virtual networks thru [[Azure VPN]] / Route Server / ExpressRoute
	- network security groups - Azure resources that contain inbound & outbound security rules to allow / block traffic based on factors (source / destination IP address, port, protocol)
	- Network virtual appliances - specialised [[Azure Virtual Machines||VMs]] that performs particular network function (e.g. running firewall, WAN optimisation)
- **connect virtual networks** - done thru virtual peering 2 virtual networks together
	- network traffic is private
	- allows resources from each virtual network to communicate
	- networks can be in separate regions
	- User-defined routes (UDR) control routing tables between subnets / virtual network -> greater control over traffic flow

Azure virtual networks support both public & private endpoints for communication between resources:
- public endpoints have public IP address -> can be accessed anywhere
- private endpoints' IP address can only be accessed within address space of a virtual network

Setting up a virtual network:
- define private IP address space thru public / private IP address ranges
