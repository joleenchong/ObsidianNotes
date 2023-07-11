Provides built-in roles to describe common access rules for [[Azure resource]]s, reducing tedium in managing permissions for every individual in a team. Custom roles can also be defined.

How is it applied:
- applied to a scope, which is a resource or set of resources that this access applies to
![[Pasted image 20230707184409.png]]
Scopes include:
- management group
- a single subscription
- resource group
- single resource

RBAC is hierarchical - when granting access to parent scope, permissions are inherited by all child scopes

Enforcement:
- enforced on any action initiated against resource passing through [[Azure Resource Manager]]
- Resource Manager provides a way to organise & secure cloud resources
- RBAC uses allow model - when role is assigned, it allows user to perform action within scope of the roe