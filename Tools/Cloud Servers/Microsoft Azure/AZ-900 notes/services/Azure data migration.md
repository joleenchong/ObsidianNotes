Azure Migrate - a service to migrate from on-premises environment to cloud:
- unified migration platform - one portal to start, run & track migration to Azure
- tools:
	- Discovery & assessment - discovers & assess servers running on VMWare, Hyper-V & physical servers to prepare for migration
	- Server Migration - migrates above + public cloud VMS & other virtualised servers to Azure
	- Data Migration Assistant - assesses SQL servers to find potential problems blocking migration (e.g. unsupported features, new features that can benefit after migration), & suggests right path for database migration
	- Azure Database Migration Service - migrates databases to Azure VMs running SQL Server / Database / Managed Instances
	- Web app migration assistant - assesses on-premise .NET & PHP web apps for migration to Azure App Service
	- Azure Data Box - move large amounts of offline data to Azure
- assessment & migration

Data Box - physical migration service to transfer large amts of data:
- secure data transfer accelerated by shipping proprietary Data Box storage device with max usable storage of 80TB
- data is automatically uploaded after Microsoft receives Data Box back
- use cases:
	- onetime migration
	- moving media library from offline tapes to Azure for online media library
	- migrating VM far, SQL server, apps to Azure
	- moving historical data to Azure for in-depth analysis & reporting using HDInsight
	- initial bulk transfer - initial transfer done using Data Box followed by incremental transfers over network
	- periodic updates
	- disaster recovery
	- security requirements
	- migrate back to on-premise or to different cloud provider

Tools for moving individual / small file groups:
- AzCopy - command line utility to copy blobs/files to/from [[Azure storage accounts]]
	- can be configured to work with other cloud providers
	- note: when synchronising, source & destination is designated & AzCopy will copy in that direction -> does not sync bi-directionally based on timestamps / other metadata
- Azure Storage Explorer - standalone GUI app to manage files / blobs in storage account
- Azure File Sync - tool to centralise file shares & keep performance & compatibility of Windows file server
	- automatically stays bi-directionally synced with files in Azure
	- uses any protocol available on Windows Server to access data locally (e.g. SMB, NFS, FTPS)
	- have as many caches as needed globally
	- replace failed local server by installing File Sync on new server in same datacentre
	- config cloud tiering so most frequently accessed files replicate locally while infrequently accessed files are kept in cloud until requested