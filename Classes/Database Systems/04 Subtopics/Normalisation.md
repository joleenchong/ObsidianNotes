When the [[03 ER modelling|ERM]] to relational mapping is done using standard process, it reduces duplicate data and avoids [[Relational schema anomalies|anomalies]] (maintains data integrity when data is updated / deleted). 

However, in complex scenarios, identifying attributes and keys to be kept in entity might not be done properly in ER.
- must check if relations are in proper form
- if any weaknesses identified, schema refinement is needed

To reduce anomalies, relations can be decomposed. Decomposing means to take out attributes from a relation to make a new relation? To decompose a relation effectively, use [[Functional dependencies|functional dependencies]] to identify keys.

Definition of terms:
- superkey - the super set of a key; a set of attributes in a relation that contains the key attributes
	- example: in relation R(A,B,C,D), {A,B}, {A,B,C}, {A,B,C,D} are superkeys
- key - a superkey with an additional property -> removal of any attributes from key will not satisfy key condition
- candidate key - each key of a relation
- primary key - the candidate key chosen to be primary key
- prime/key attribute - an attribute which is a member of a candidate key
- non-prime/key attribute - an attribute which is not a member of a candidate key