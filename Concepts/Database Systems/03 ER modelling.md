
Entity Relationship Model (ERM):
- [[Components of an ERM]]
- [[Drawing an ER diagram]]
- Diagrams:
	- Note: draw out ER diagram as example
	- Entity set - rectangle
		- weak entity set - double rectangle
			- composite attributes for weak key - underlined + dotted line
		-  subtypes - arrow pointing from supertype to subtype
	- Attribute - ovals
		- key attributes - text underlined
		- multi-valued attributes - double line oval
		- derived - dotted line oval
		- composite - simple attribute ovals connected to the composite attribute oval by a line
	- relationship - diamond with lines to each entity set. Text 
		- put drawings for binary, unary relationship
		- unary relationship - the entity instance has different roles in relationship
		- cardinality constraint - the maximum number of relationships an entity can participate
			- either 1 (1) or many (N)
			- binary relationships cardinality:
				- one to one (1:1)
				- one to many (1:N)
					- digest this example - relationship Works between Employee and Department. An employee can work in at most 1 department, and a department can have many employees working in it
				- many to many (M:N)
			- ternary cardinality:
				- one to one to one (1:1:1)
				- one to one to many (1:1:N)
				- one to to many to many (1:N:M)
				- many to many to many (M:N:P)
			- Insert drawing of Chen's notation of cardinality
			- slide 30 for diagram
		- participation constraint - the minimum number of entities that can have a relationship with another entity
			- two values:
				- total participation - an entity can't exist without another entity
				- partial participation - entity doesn't need to have relationship to another entity to exist
				- analogy - in a polycule, if every member is dating each other, that's total participation. If a member is dating someone who is not dating other members of the polycule, then that's partial participation
			- insert drawing (slide 34)
		- relationship attributes - ovals connecting to relationship
		- weak relationship - double diamond
Slide 40 explanation -  customer reads books by certain authors

Questions:
What is that triangle?? Oh wait subtype?
Can key attributes have more than 1 value? nope lol it'll be covered next lecture in more details
If relationships can be entities, can relationships also have relationships with other relationships? nope