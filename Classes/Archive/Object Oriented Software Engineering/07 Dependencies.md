High number of dependencies affect:
- maintainability - harder to understand / change code
- testability - more complex test cases, harder to figure out test results

Dependency injection:
- a class should not hard-code its dependencies -> easy class replacement
	- no direct object creation (`new` keyword in java)
		- does not apply to standard API classes
	- no static method calls to other classes
	- no raw objects (C++)
	- references to required objects must be imported
	- constructor should be trivial -> significant code in methods
- a piece of code (the injector) connects objects together by:
	- makes actual objects, supplies dependencies -> done in main / close to main
![[Pasted image 20240506154426.png]]
- creation of equation and graphics objects are made in main

Patterns:
[[Factory method]]
[[Singleton pattern]]