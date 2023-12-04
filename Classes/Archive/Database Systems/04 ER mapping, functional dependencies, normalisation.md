Quick reference:
![[Converting_ER_diagram_to_DB_Schema.pdf]]
![[Normalisation_intro.pdf]]

---
ER mapping is about translating the [[03 ER modelling|ERM]] to a SQL schema.

Foreign keys (FK): keys imported from another database so that it can maintain the relationship between 2 entities

Referential integrity constraints: maintains consistency among tuples -> enforced by foreign keys

Steps to mapping ER model to relational schema:
1. Map entities
2. Map 1:N relationships
	- for each n-side entity type:
		- add primary key of 1-side entity type -> becomes foreign key
		- if there are descriptive attributes in relationship, add them
	- if relationship is recursive, primary key of 1-side entity type is annotated with role name
3. Each M:N relationship type becomes a separate relation
	- add primary key of participating entity types to relation  -> becomes foreign keys
	- add all descriptive attributes of relationship type to relation
	- primary key of relation consist of primary keys of two participating entities
	- for recursive M:N, two roles are annotated with role name
4. Each 1:1 relationship can be combined with either side of entity type or can be treated like 1:N relationship type
	- if both sides of relationship are with partial participation, two entities becomes two relations 
5. A weak entity type becomes a relation that includes the primary key of identifying owner entity type
	- primary key of relation consists of foreign key and discriminator 
6. Each [[ternary relationship]] type becomes a separate relation
	- primary keys of participating entity types become foreign keys
	- add descriptive attributes of relationship type to relation 
	- primary key of relation consists of 3 participating entity types when cardinality is many-to-many
	- when not many-to-many, primary key of relation consists of at least 2 foreign keys -> all foreign keys coming from side entity types must be included in relation's primary keys

![[Pasted image 20230815150229.png]]
![[Pasted image 20230815150739.png]]
![[Pasted image 20230815151134.png]]

is-A relationships:
- create a relation for super type
- create relation for each sub types of supertype & include primary type as a FK in subtype's relations

Multi-value attributes - not supported, handled by:
- keep values of multi-valued attribute in multiple tuples of relation
- add fixed number of additional attributes to relation to keep multiple values
- make separate relation to keep multi-valued attributes and link to other relation thru foreign key

Usually, mapping from ERM to [[Normalisation|normalised]] database models -> must use data dictionary, data catalogue and business rules to properly implement

Questions and notes:
- Double diamonds are relationship sets linked to weak entity sets
