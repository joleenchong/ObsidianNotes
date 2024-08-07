State:
- any runtime info:
	- variable / field values, object types
	- instruction pointer (current execution location)
	- external info (e.g. files, libs, OS, hardware)
- a distinct 'mode' / set of behaviour represented by some runtime info
- continues even when nothing is happening
- always take some time
- ends only when something happens

Each state has:
- incoming transmissions from other states
- outgoing transmissions to other states

State diagrams:
![[Pasted image 20240512221640.png]]
![[Pasted image 20240512221716.png]]
![[Pasted image 20240512221741.png]]
![[Pasted image 20240512221757.png]]

Representing states:
- for 2 states, booleans
- for >2 states:
	- symbolic constants
	- enums
	- special values (like null)
	- combination of fields
```java
//Constants
public static final int STATE1 = 0;
public static final int STATE2 = 1;
public static final int STATE3 = 2;
private int state = STATE1;
//Enums
public enum State {
	STATE1, STATE2, STATE3;
}
private SomeType state = State.STATE1;
```

Patterns:
- [[State pattern]]