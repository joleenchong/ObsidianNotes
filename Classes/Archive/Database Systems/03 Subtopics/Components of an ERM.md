3 components:
- Entities
- Relationships
- Attributes

Entities - an object that can be distinctly identified:
- entity set / type - a collection of similar entities
	- weak entity set - does not have its own unique key
		- key is always composite
		- key format: primary key of owner entity set + partial key / discriminator of weak entity
- sub/supertypes - a subtype of an entity inherits all the attributes of the supertype, but it has some distinct attributes the supertype doesn't have

Relationships - an association among entity sets:
- can be treated as entities (has their own attributes and stuff)
- 3 types:
	- unary - an association of 1 entity set with itself
	- binary - an association btwn 2 entity sets
	- ternary - an association btwn more than 2 entity sets
 
Attributes - common characteristics of an entity set / relationship
- 2 types:
	- identifying / key - unique attributes (e.g. ID)
		- some key attributes can be shared btwn entities, but not all
	- descriptive - nonunique attribute
- multi-valued attributes - multiple values instead of a single one for each entity instance (e.g. multiple telephone numbers)
	- key attributes cannot be multi-valued
- derived attributes - attributes may have values derived based on other attributes (e.g. average calculated from other attributes)
	- these attributes are not stored
- composite attributes - attributes made out of several simple attributes (e.g. full name made up of first name and surname)

 