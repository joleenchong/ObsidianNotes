A comma-separated list.
- each item is in the form `[<mode>] <name> <type>`
	- mode:
		- IN - procedure uses value, does not change value. default when no mode specified
		- OUT - procedure changes value, does not use.
			- has initial value of NULL -> value is assigned to it during procedure -> new value passed back to calling program
		- IN OUT - both
	- names are not case-sensitive
	- functions cannot specify parameter mode, parameters can only be IN