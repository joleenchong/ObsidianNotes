To start MySQL on WSL: 
```bash
sudo mysql -u root
```

Select database to work in:
```MySQL
USE <database>;
```

Display all databases:
```MySQL
SHOW DATABASES;
```

Show error details:
```MySQL
SHOW ERRORS;
```
# Tables
Create relation:
```MySQL
CREATE TABLE <name> (
	<list of elements>
);
```

Delete relation:
```MySQL
DROP TABLE <table_name>;
```

Adding new attribute to existing relation:
```MySQL
ALTER TABLE <name> 
	ADD <new attribute name> <type>
;
```
- when adding, all values of new attribute will be NULL -> set DEFAULT value to avoid

Deleting column:
``` MySQL
ALTER TABLE <name>
	DROP COLUMN <attribute name>
;
```

Describes table attributes:
```MySQL
DESC TABLE;
```
## Constraints
Declaring key attribute:
``` MySQL
CREATE TABLE Book (
	isbn INT(13) PRIMARY KEY,
	title VARCHAR(50),
	author VARCHAR(50)
);
-- can also be declared on separate line
CREATE TABLE Book (
	isbn INT(13),
	title VARCHAR(50),
	author VARCHAR(50),
	PRIMARY KEY(isbn)
);
-- Primary key includes multiple attributes
CREATE TABLE Writes(
	author_name VARCHAR(50),
	book_id INT(13),
	pub_date DATE,
	PRIMARY KEY(author_name, book_id)
);
```

NOT NULL constraint:
```MySQL
CREATE TABLE Book(
	isbn INT(13),
	title VARCHAR(50) NOT NULL,
	author VARCHAR(50),
	PRIMARY KEY(isbn)
);
```
- note: when comparing, do not use = NULL -> use IS NULL

FOREIGN KEY constraint:
```MySQL
CREATE TABLE OtherTable (
	id CHAR(3)
);
CREATE TABLE Example (
	id CHAR(3),
	CONSTRAINT FK_id FOREIGN KEY (id) REFERENCES OtherTable(id)  
);
```

# Tuples
Inserting rows (tuples):
```MySQL
INSERT INTO <relation>
VALUES(<list_of_values);
```
- values must be listed in column sequence
- example (name, ID, date of purchase, cost):
``` MySQL
insert into Purchases
values ('Charlie Brown', 97803120, '2021-04-13 14:22:01', 32.99);
```
- when inserting missing data:
```MySQL
insert
into Purchases (cus_name, book_id, cost)
values ('Peter Pan', 23425592, 12.50 );
```
- date is null
- Default values example:
```MySQL
CREATE TABLE Purchases (
	cus_name VARCHAR(30),
	book_id CHAR(13),
	p_date DATE,
	cost DECIMAL (6,2)
		DEFAULT 99.99,
);
```
- when cost is left empty in insertion, it will use the value 99.99
Retrieving data:
```MySQL
SELECT < attribute1, attribute2, ...>
FROM <relation>
WHERE <condition>;
```
- example:
```MySQL
select cus_name, book_id
from Purchases
where cost>25;
```

Delete tuple:
- deleting all tuples satisfying condition:
```MySQL
	DELETE FROM <relation>
	WHERE <condition>;
```
- delete all tuples:
```MySQL
DELETE FROM <relation>;
```

Modify tuple:
```MySQL
UPDATE <relation>
SET <list of attributes assignmnts>
WHERE <condition_on_tuples>
```

# Querying

```MySQL
SELECT cus_name, book_id
FROM Purchases
WHERE cost>25;
```

Refer to [[05 Joins, grouping, sorting]] for JOIN.

# Files
Running SQL file:
```MySQL
\. file.sql
```

Outputting MySQL command log:
```MySQL
tee commands.out
-- OR
\t commands.out
```