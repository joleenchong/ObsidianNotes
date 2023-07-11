How Azure stores data on the cloud. Services offered depends on [[Azure storage accounts]] type.

Services:
- **Blobs** - a scalable object storage solution to store massive amounts of unstructured data (e.g. text / binary data)
	- used for multimedia (images, documents, video, audio) transfer & disaster recovery
	- Data Lake Storage Gen2 allows for big data analytics
	- accessed by URLS, Azure REST API, Azure PowerShell, Azure CLI or Storage client library
	- Access tiers:
		- hot - for data accessed frequently (e.g. website images)
		- cool - infrequently accessed data stored for at least 30 days (e.g. customer invoices)
			- lower [[Surface Level Agreements]] & higher access costs compared to hot data for lower storage costs
		- archive - rarely accessed data stored for at least 180 days (e.g. long-term backups)
			- can store data offline and lowest storage cost but highest costs to rehydrate and access data
	- only hot & cool tiers can be set at account level -> archive access tier not available at account level
	- all tiers can be set at blob level during or after upload
- **Files** - fully managed file storage for cloud / on-premise deployments
	- accessible via Server Message Block (SMB) / Network File System (NFS) protocols
	- file shares mounted concurrently by cloud / on-premise
	- SMB - accessed from Windows, Linux, macOS clients and can be cached on Windows Servers thru Azure File Sync for fast access
	- NFS - accessed from Linux / macOS
	- Benefits:
		- shared access - can replace on-premise file shares with Azure file shares without worrying abt app compatibility
		- fully managed - no need to manage hardware / OS
		- scripting & tooling - PowerShell cmdlets & Azure CLI used to create, mount & manage Azure file shares. Portal & Storage Explorer can create & manage file shares
		- resiliency - always available
		- familiar programmability - apps running in Azure can access data in share via file system I/O APIs / client libraries / REST API
- **Disks** - used by [[Azure Virtual Machines]] and apps to simulate physical disks; has SSD and HDD options
- Tables - a noSQL solution for storing key-value pairs in large datasets
- **Queues** - a service for storing large numbers of messages
	- used to create a backlog of work to process asynchronously
	- can be combined with [[Azure Functions]] to take action when message is received

Benefits:
- durable & highly available thanks to redundancy
- secure - all data encrypted and lots of control over data access
- scalable
- managed - handles hardware maintenance, updates & critical issues
- accessible - accessed anywhere with HTTP / HTTPS and client libraries provided in variety of languages

Redundancy:
- multiple copies of data stored to protect from disasters
- Factors for determining redundancy options:
	- how data is replicated in primary region
	- whether data is replicated to second region geographically far from primary region (for regional disasters)
	- whether app needs read access to replicated data in secondary region if primary region becomes unavailable
- data in account is replicated 3 times in *primary region*. 2 options for how this is done:
	- Locally-redundant storage **(LRS)** - replicates data 3 times within single datacentre in primary region
		- at least 11 nines (99.9999999%) durability over given year
		- lowest cost but least durability
		- protects against server rack & drive failures but data could be lost if disaster affecting whole datacentre occurs
	- Zone-redundant storage **(ZRS)** - For [[Azure regions]] with availability zones, replicates data synchronously across 3 availability zones in primary region
		- at least 12 nines (99.9999999999%) over given year
		- data still accessible for read / write operations if zone becomes available
		- for scenarios that need high availability & restricting replication of data within country / region for data governance requirements
- 2 options for copying data to secondary region:
	- Geo-redundant storage **(GRS)** - like running LRS in 2 regions
		- at least 16 nines (99.99999999999999%) durability over given year
	- Geo-zone-redundant storage **(GZRS)** - like ZRS in primary and LRS in secondary
		- at least 16 nines (99.99999999999999%) durability over given year
	- data in secondary region isn't available for read / write access UNLESS failover to secondary region ->changes region to primary
		- data in secondary is read only
	- Note: as data is replicated to secondary region asynchronously, failure affecting primary can cause data loss if primary region can't be recovered
		- recovery point objective - (RPO) interval btwn most recent writes to primary and last write to secondary
		- Storage usually has RPO of <15mins
- Read access to secondary region data can be enabled to keep data always available thru enabling read-access geo-redundant storage **(RA-GRS)** or read-access geo-zone-redundant storage **(RA-GZRS)**