Prevents [[Azure resource]]s from getting accidentally deleted / changed. They can be applied to individual resources, resource groups, subscriptions, and they can be inherited.

Types:
- Delete - authorised users can still read & modify but cannot delete
- ReadOnly - authorised users can read but cannot delete or modify

How to manage:
- done thru Azure portal, PowerShell, Azure CLI, [[Azure Resource Manager]] template

To modify a locked resource, lock must be removed.