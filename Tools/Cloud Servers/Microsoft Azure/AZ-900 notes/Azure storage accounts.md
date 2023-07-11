A storage account provides unique namespace for [[Azure Storage]] data, globalising access over HTTP / HTTPS. When creating account, the type of the account determines storage services & redundancy options, impacting use cases.

List of redundancy options:
- Locally redundant storage (LRS)
- Geo-redundant storage (GRS)
- Read-access geo-redundant storage (RA-GRS)
- Zone-redundant storage (ZRS)
- Geo-zone-redundant storage (GZRS)
- Read-access geo-zone-redundant storage (RAGZRS)

| Type of account             | Supported services                                                          | Redundancy options                  | Usage                                                                                                                                                    |
| --------------------------- | --------------------------------------------------------------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standard general-purpose v2 | Blob Storage + Data Lake Storage, Queue Storage, Table Storage, Azure Files | LRS, GRS,RA-GRS, ZRS, GZRS, RA-GZRS | Standard type for blobs, file shares, queues & tables. For most scenarios using Azure Storage                                                            |
| Premium block blobs         | Blob Storage + Data Lake Storage                                            | LRS, ZRS                            | Premium type for block blobs & append blocks. For high transaction rates / smaller objects / consistently low storage latency                            |
| Premium file shares         | Azure Files                                                                 | LRS, ZRS                            | Premium type for file shares only. For enterprise / high-performance scale apps. Use if Server Message Block (SMB) & NFS file shares support both needed |
| Premium page blobs          | Page blobs only                                                             | LRS                                 | Premium type for page blobs only                                                                                                                         |

Storage account endpoints:
- every storage account in Azure must have unique-in-Azure account name
- combination of account name and Storage service endpoint forms storage account endpoints
- Rules for naming:
	- name length must be btwn 3 and 24 characters and only have numbers and lowercase letters
	  

