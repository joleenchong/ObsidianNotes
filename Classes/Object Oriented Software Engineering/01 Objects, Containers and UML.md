Object Orientation purpose:
- helps divide and conquer large-scale software design

Concepts:
- [[Encapsulation]] - outside world must not see / know how a class works on the inside
- [[Inheritance]] - some classes are special types of other classes
- [[Polymorphism]] - different classes can be used in same situation if they have common interface

Language differences:
- Typing:
	- static typing - compiler knows what type things are -> datatypes must be written in program
		- datatypes can be worked out by compiler if they have type inference
		- helps prevent whole categories of bugs
		- can often be convoluted
	- dynamic typing - compiler doesn't know what types are
		- can risk type errors
- Inheritance:
	- single-inheritance-with-interfaces (e.g. Java, C#) - classes extend one other class (super / base class) & implement zero or more interfaces
	- multiple inheritance (e.g. Python, C++) - classes extend zero or more other classes
- Access modifiers:
	- python just uses honour system - starts fields and methods with _
- Constructors and destructors:
	- Java, C#, C++ - looks like a method but isn't
	- Python - a normal method called \_\_\init\_\_()
	- C++ - has destructors to clean up object resources when it needs to be deleted

Class design:
- objects - have fields and methods
- class - a set of objects that share the same behaviour
	- superclass - a superset of objects that share some of the same behaviour
	- subclass - a subset of objects that share some of the same behaviour

Bad class design:
- can't think of good name for class and its methods -> no specific purpose
- one massive class and numerous tiny ones -> a god class with too many responsibilities
- one class knows too much about another -> high coupling -> takes more time to inspect, test, modify affected code
- one class accesses another class's data a lot -> feature envy -> better to keep data in same class as logic that needs to access it

UML:
- 2 categories:
	- structural diagrams - shows parts of system (e.g. class, object diagrams)
	- behavioural diagrams - shows actions (e.g. sequence, state, use case diagrams)
- Class diagrams:
	- add diagrams from 5.4

[[Containers]]
[[Iterator pattern]]