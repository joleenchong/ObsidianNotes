The ability to execute an operation on an object.

Format: <object-name, right-set>
- right-set - a subset of all valid operations that can be performed on object

Revocation of access rights:
- properties:
	- immediate / delayed - time taken for revocation to take effect
	- selective / general - selection of users to revoke rights from
	- partial / total - selection of rights to revoke
	- temporary / permanent - whether access can be given back later or never
- [[access matrix||access list]]:
	- search access rights to revoke and delete form access list
	- properties of revocation:
		- immediate
		- general / selective
		- total / partial
		- permanent / temporary
- capability list:
	- schemes:
		- reacquisition - deletes capabilities for a domain periodically
			- process can reacquire deleted capability if access is not revoked
		- back-pointers - use list of pointers for each object to all capabilities for object
			- costly
		- indirection - capability points to unique entry in global table -> points to object
			- does not allows selective revocation
		- keys