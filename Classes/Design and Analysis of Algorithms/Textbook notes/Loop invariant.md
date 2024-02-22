Loop invariants are properties of a loop that are true before and after each loop.

Loop invariants must have 3 properties:
- **initialisation** - true prior to first loop
- **maintenance** - if true before current loop, remains true before next loop
- **termination** - when loop terminates, gives useful property to show algo is correct
	- most important to show correctness

When first 2 properties are true, the loop invariant is true prior to every loop (similar to mathematical induction -> a method for proving a statement is true for every natural number).
