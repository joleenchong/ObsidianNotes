VMs provide [[Infrastructure as a Service (IaaS)]] as a virtualised server and can be used like a physical computer -> customise software running on VM.
Used if need:
- total control over OS
- ability to run custom software
- use custom hosting configurations

As an IaaS offering, software on VM must still be configured, updated and maintained.

Image - a template for creating a VM including an OS and other software
VMs can be quickly made and provisioned through preconfigured images.

A single VM can be run for testing, development, or minor tasks. VMs can be grouped together for high availability, [[Cloud scalability||high scalability]], and redundancy.

VM scale sets:
- creates and manages a group of identical, load-balanced VMS automatically
- number of VM instances automatically increase / decrease depending on demand OR can scale based on defined schedule
- deploys load balancer to ensure resource efficiency

VM availability sets:
- groups VMs thru update domain & fault domain:
	- update domain - groups VMs that can be rebooted at the same time
	- fault domain - groups VMs by common power source & network switch

Examples of VM use:
- testing and development
- running apps on cloud
- extending own datacentre to cloud
- disaster recovery

Azure also provides Azure Virtual Desktop. This is different from Azure VMs in that Desktop provides a virtual Windows desktop, whereas VMs are simply infrastructure that can also choose between Windows and Linux