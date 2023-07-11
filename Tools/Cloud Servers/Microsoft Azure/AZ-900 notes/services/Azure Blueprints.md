Azure Blueprints standardises cloud subscriptions or environment deployments by defining repeatable settings & policies applied for new created subscriptions + deploy new test / dev environments with pre-configured security & compliance settings.

Artifact - a component in the blueprint definition
- artifacts can have no parameters or one or more parameters to config
- parameter value can be specified at blueprint definition creation / assign blueprint definition to scope
- examples:
	- role assignments
	- policy assignments
	- [[Azure Resource Manager]] templates
	- resource groups

How it monitors deployment:
- version-able - after creating initial config, can be updated and assigned new version to update
- relationship between blueprint definition (what should be deployed) & blueprint assignment (what was deployed) is preserved -> tracks & audits deployments

