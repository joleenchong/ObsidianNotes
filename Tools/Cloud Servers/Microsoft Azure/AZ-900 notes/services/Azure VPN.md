Virtual Private Networks (VPN):
- uses an encrypted tunnel within another network
- connect 2+ trusted private networks over untrusted network (i.e. public internet)
- untrusted network traffic is encrypted

VPN gateway:
- a type of [[Azure virtual networks||virtual network]] gateway
- deployed in dedicated subnet of virtual network for following connectivity:
	- connect on-premise datacentres to virtual networks thru site-to-site
	- connect devices to virtual network thru point-to-site
	- connect virtual networks to other virtual networks thru network-to-network
- can only deploy 1 VPN gateway per virtual network BUT can use one gateway to connect to multiple locations (e.g. other virtual networks / on-premise datacentres)
- gateways are deployed as 2 instances in active / standby config by default
- when deploying, specify VPN type:
	- Policy-based - specifies statically packets' IP addresses to be encrypted thru each tunnel & evaluates every data packet against sets of IP addresses to choose tunnel to send package
	- Route-bases - IPSec tunnels are modelled as network / virtual tunnel interface & IP routing statically / dynamically decides with interface to use for sending each package
		- preferred for on-premise devices
		- more resilient to topology changes (e.g. new subnets)
		- coexists with [[Azure ExpressRoute]]

Keeping VPN highly available:
- Active / standby - when planned maintenance / unplanned disruption affects active instance, standby instance assumes responsibility for connections without user intervention
	- connections interrupted during failover but restored quickly
- Active / active - unique public IP address is assigned for each instance with separate tunnels from on-premise devices to each IP address
	- availability can be extended by deploying extra VPN devices on-premise
- ExpressRoute failover - config VPN gateway as failover path for ExpressRoute connections (so both physical and virtual connection)
	- ExpressRoute circuits are resilient but weak to physical problems affecting cables
- Zone-redundant gateways - deploying gateways in regions that support availability zones
	- physically & logically separates gateways within region to protect on-premise network connectivity from zone-level failures
	- need different gateway stock keeping units (SKUs) & use Standard public IP addresses instead of Basic public IP addresses
