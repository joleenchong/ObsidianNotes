Deny [[Mutual Exclusion]]:
- not required for sharable resources
- not possible as some resources are non-sharable (like some I/O devices)

Deny [[Hold & Wait]]:
- Options:
	- each process granted all resources before it starts
	- allow process to request resources only when it has none
- Problems:
	- resource utilisation is low
	- possible starvation of resources

Prevent [[No pre-emption]]:
- process requesting resources pre-emptively must release all currently held resources
- hard to apply to processes that can't save state easily

Deny [[Circular Wait]]:
- resource types are ordered
- process can only request resource of higher order than previous resource requested
- may be impossible to find resource ordering that satisfies everyone

