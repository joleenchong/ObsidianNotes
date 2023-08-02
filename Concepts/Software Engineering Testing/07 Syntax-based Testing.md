
- tests are created with two general goals:
	- *cover* the syntax in some way
	- *violate* the syntax (invalid tests)

BNF - Backus-Naur Form
Grammar:
- Recognizer - basically it's parsing
- Generator - given a grammar, derive strings in the grammar

Coverage criteria:
- **Terminal Symbol Coverage (TSC)** - TR contains each terminal symbol *t* in the grammar G
- **Production Coverage (PC)** - TR contains each production *p* in the grammar G
	- PC subsumes TSC
- **Derivation Coverage (DC)** - TR contains every possible string that can be derived from the grammar G -> impractical
- number of TSC tests bound by number of terminal symbols
- number of PC tests bound by number of productions
- number of DC tests depend on details of grammar

Mutation testing:
- fundamental premise - if the software contains a fault, there will usually be a set of mutants that can only be detected by a test case that also detects that fault
- *mutant* - a variation of valid string that is the result of one application of mutation operator
	- can be valid or invalid strings
- Ground string - a string in the grammar
	- when mutated to make valid strings, mutations should  exhibit different behaviour from ground string
- Mutation Operator - a rule that specifies syntactic variations of strings generated from a grammar
	- should not apply more than one operator at the same time -> multiple mutations can interfere with each other
	- every possible application of mutation operator must be considered with program-based mutation
- killing mutants: finding tests that cause mutants to fail when executed
- **Mutation Coverage (MC)** - coverage in mutation equates to number of mutants killed -> mutation score
- Mutation Operator Coverage (MOC) - make sure every specified operator is used
- Mutation Production Coverage (MPC) - take notes
- Number of test requirements for mutation depends on:
	- syntax of artifact being mutated
	- mutation operators

Syntax-based testing on Programs:
- BNF criteria used to test compilers
- mutation testing criteria most common for unit testing & integration testing of classes
- types of mutants:
	- dead mutant - killed by a test case
	- stillborn mutant - syntactically illegal
	- trivial mutant - almost every test can kill it
	- equivalent mutant - no test can kill it
- RIP mode:
	- **Reachability** - test causes faulty statement to be reached
	- **Infection** - test causes faulty statement to result in incorrect state
	- **Propagation** - incorrect state propagates to incorrect output
	- leads to 2 variants of mutant killing:
		- Strongly killing mutants: take notes
		- Weakly killing mutants: satisfies reachability and infection but not propagation
- Weak Mutation Coverage: take notes
	- named weak mutation as it is easier to kill mutants under this assumption
	- requires less analysis

 continue from slide 38

Bomb() makes code crash -> checks if code section is reachable