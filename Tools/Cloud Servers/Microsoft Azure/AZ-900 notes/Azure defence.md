Zero Trust Model:
- A security model that assumes the worst case scenario and protects resources with that expectation.
- Guiding principles:
	- verify explicitly - always authenticate & authorise based on all available data points
	- use least privilege access - limit user access with Just-In-Time & Just-Enough-Access, (JIT / JEA), risk-based adaptive policies, data protection
	- assume breach - minimise blast radius & segment access, verify end-to-end encryption, use analytics to get visibility, drive threat detection, improve defenses

Defence-in-depth:
- objective: protect info & prevent it from being stole by unauthorised access
- multiple layers of defence:
	- physical security - protect computing hardware in datacentre
	- identity & access - ensure identities are secure & least privilege access in place
		- control access to infrastructure & change control
		- use [[Azure authentication methods|SSO & multifactor authentication]] 
		- audit events & changes
	- network perimeter - protect from network-based attacks against resource
		- use distributed denial of service (DDoS) protection to filter large-scale attack before they can affect users
		- use perimeter firewalls to identify & alert on malicious attacks against network
	- network - limit network connectivity across all resources to allow only what's needed and reduce risk of attack spreading to other systems in network 
		- limit communication btwn resources thru segmentation & access controls
		- deny by default
		- restrict inbound internet access & limit outbound access where appropriate
		- implement secure connectivity to on-premise network
	- compute - secure compute resources & have proper controls in place to minimise security issues
		- secure access to virtual machines
		- implement endpoint protection on devices & keep systems patched & current
	- app - reduce number of vulnerabilities in code
		- ensure apps are secure & free of security vulnerabilities
		- store sensitive app secrets in secure storage medium
		- make security design requirement for all app development
	- data - controls access to business & customer data that must be protected

Defender for Cloud:
- a monitoring tool for security posture management & threat protection
- an Azure-native service - many services are monitored & protected without needing deployment
- can deploy Log Analytics agent to gather security-related data
	- directly for Azure machines
	- for hybrid & multicloud, Defender plans are extended thru [[Azure Arc]]
- detects threats across:
	- Azure PaaS services - detect threats targeting services like [[Azure App Service]], Azure SQL, [[Azure storage accounts]], other data services + anomaly detection on activity logs
	- Azure data services - helps automatically classify data in Azure SQL + assessments for potential vulnerabilities in SQL & [[Azure Storage]] + migration recommendations
	- Networks - limit exposure to brute force attacks by using just-in-time VM access for security + set access policies on selected ports
- fills 3 vital needs:
- ![[Pasted image 20230707200912.png]]
