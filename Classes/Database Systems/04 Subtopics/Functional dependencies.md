Functional dependencies are relationships that exist when one attribute uniquely determines another attribute.
- like a many-to-one relationship from one set of attributes within given relation
- can occur btwn 1 attribute and another or btwn multiple attributes
- considered *trivial* if cannot be failed to be satisfied; right side is subset of left side
- a dependency X->Y is considered *full* if removal of any attribute from X means that dependency does not hold anymore
![[Pasted image 20230815163812.png]]

Notation:
`{Determinant attribute} -> {dependent attribute}` or 
`Determinant attribute -> dependent attribute`

Key constraints are special cases; in X->Y, attributes in key play role of X and set of all attributes play role of Y.
![[Pasted image 20230815164715.png]]

![[Pasted image 20230815165453.png]]

Normal forms:
- describes a relational schema that adheres to certain criteria
- types:
	- 1st normal form (1NF) - the relation in 1NF has no decomposable attributes and attributes are functionally dependent on key
		- example: slide 41
	- 2nd normal form (2NF) - every nonprime attribute in relation is not partially dependent on any key of relation
		- implicitly in 1NF
		- example: slide 43 & 44
	- 3rd normal form (3NF) - no nonprime attribute is transitively dependent on any key
		- transitively dependent - X->Y is transitively dependent when there is a set of non-key attributes Z and both X->Z and Z->Y holds
		- implicitly in 2NF
		- example: slide 46-48
	- Boyce Codd normal form (BCNF) - every non-trivial FD satisfied by relation is determined by superkey(s) of relation
		- example: slide 50-51