Database Management System - a software system to manage databases
- functionalities:
	- create new database
	- query data
	- stores large volume of data
	- durability of database
	- multi-user concurrent access

Data model - a notation for describing data with 3 parts:
- structure
	- e.g. relational models - tables, semi-structured model = trees / graphs
- operations on data
- constraints

Relational data model:
- structure - table consisting of relation name, attribute names
- operations - queries, based on relational algebra
- constraints - key, referential integrity
![[Pasted image 20230721155418.png]]
- Relation schema - a relation name and attribute list
	- e.g. Book (title, author) / Book(title:varchar(30), author:varchar(60))
- database - a collection of relations
- database schema - a set of all relation schemas in database
- To represent data, model and identify info using:
	- [[entity-relationship diagram]]s (ER model)
	- UML diagrams
- Entity - a collection of things (e.g. Books)
- Relation - a connection btwn 2 or more entities

Structured Query Language (SQL) - a query language
- components:
	- schema definition
	- data retrieval
	- data modification
	- indexes, constraints
	- views, triggers
	- transactions, authorisation, etc.
- Two aspects:
	- Data-definition sub language (DDL) - declares database schema
	- Data manipulation sub language (DML) - queries data

Data types:
- INT / INTEGER
	- consists of SMALLINT, BIGINT, etc.
- REAL / FLOAT - approximate numbers
- DECIMAL \[(n\[,m])] - total n digits of which m are to the right of the decimal point
- CHAR (n) - fixed length character string, padded with blanks
- VARCHAR (n) - variable-length strings up to n characters
- DATE, TIME & DATETIME

Identifiers:
- starts with a letter followed by alpha-numeric characters
	- MySQL allows identifiers to start with non-character but cannot be entirely numbers
	- allows $ & _ depending on whether string is quoted
- can't have identical names

Questions:

