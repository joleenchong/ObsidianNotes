- *predicate* - an expression that evaluates to boolean value
	- can contain:
		- boolean variables
		- non-boolean variables that have boolean operators (>, <, >=, <=, !=)
		- boolean function calls
- List of logical operators:
	- ¬ – the negation operator 
	- ∧ – the and operator 
	- ∨ – the or operator 
	- → – the implication operator 
	- ⊕ – the exclusive or operator 
	- ↔ – the equivalence operator
- *clause* - a predicate with no logical operators
Example: (a < b) ∨ f (z) ∧ D ∧ (m >= n *x* o)
- Four clauses:
	- (a < b) - relational expression
	- f (z) - boolean-valued function
	- D - boolean variable
	- (m >= n *x* o) - relational expression

Abbreviations:
- *P* - set of predicates
- *p* - single predicate in *P*
- *C* - set of clauses in *P*
- *Cp* - set of clauses in predicate *p*
- *c* - single clause in *C*

Coverages:
- Predicate coverage - every *p* must evaluate to true and false
- Clause coverage -  every *c* must evaluate to true and false
	- does not cover PC and vice versa
- Combinatorial Coverage (CoC) - requires every possible combination
- General Active Clause Coverage (GACC) - for each major clause c, choose minor clauses such that c determines the predicate
	- clause c has to evaluate to true and false
	- minor clauses do not need to be the same
p = a ∧ (b ∨ c)

| row | a   | b   | c   | P   | Pa  | Pb  | Pc  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **1**   | T   | T   | T   | T   | T   |     |     |
| **2**   | T   | T   |     | T   | T   | T   |     |
| **3**   | T   |     | T   | T   | T   |     | T   |
| 4   | T   |     |     |     |     | T   | T   |
| **5**   |     | T   | T   |     | T   |     |     |
| **6**   |     | T   |     |     | T   |     |     |
| **7**   |     |     | T   |     | T   |     |     |
| 8    |     |     |     |     |     |     |     |
Major clause: a
Pa = T, a = T; Rows 1, 2, 3
Pa = T, a = F; Rows 5, 6, 7
Set of possible test requirements: { (1,5), (1,6), (1,7), (2,5), (2,6), (2,7), (3,5), (3,6), (3,7) }
![[Pasted image 20230601194402.png]]
![[Pasted image 20230601194408.png]]
- Restricted Active Clause Coverage (RACC) - choose minor clauses such that *c* determines the predicate
	- minor clauses must be the same
	- often leads to infeasible test requirements

![[Pasted image 20230601194418.png]]
