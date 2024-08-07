![[Pasted image 20240512222734.png]]
![[Pasted image 20240512223514.png]]
Each state is a separate class -> breaks up a class into multiple states. During a state transition, the state object is replaced by another.

Components:
- context object - owns 1 state object
	- delegates state-dependent operations to state object
- state object interface
- states that implement state object

Benefits:
- don't need so much if else switch statements -> good for no brain hurty
