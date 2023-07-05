**Topics**
- terminology
-------------
# Terminology
- Software fault - a static defect in software
- Software error - an incorrect internal state that is the manifestation of some fault
- Software failure - external, incorrect behaviour with respect to requirements or other description of expected behaviour
- Testing - finding inputs that cause software to fail
- Debugging - the process of finding a fault given a failure
- Software observability - how easy is it to observe behaviour of program in terms of its outputs, effects on environment, and other hardware and software components
	- software affecting hardware devices / databases / remote files have low observability
- controllability - how easy is it to provide a program with needed inputs in terms of values, operations, and behaviour
	- easy to control software with inputs from keyboards
	- inputs from hardware sensors or distributed software is harder
	- data abstraction reduces controllability and observability

For a failure to be observed - 
1. Reachability - location(s) in program that contain fault must be reached
2. Infection - state of program must be incorrect
3. Propagation - infected state must propagate to cause some output of program to be incorrect

Logical expressions coverage:
- Predicate Coverage - each predicate must be true and false
- Clause Coverage - each clause must be true and false
- Combinatorial Coverage - various combinations of clauses
	- Active Clause Coverage - each clause determine the predicate's result
