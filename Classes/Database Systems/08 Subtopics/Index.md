A data structure for quick access to tuples, given values of one or more attribute.
- faster than reading a row sequentially (like hash tables vs linked lists)
- implemented through a B-tree

Declaring:
```mysql
CREATE INDEX <name>
ON <table_name_>(<attribute_list>);
```

Using index example:
```mysql
CREATE INDEX HardInd ON Hardcover(jacket);
CREATE INDEX BookInd ON Books(title);

SELECT isbn,title FROM BOOKS NATURAL JOIN Hardcover
WHERE title LIKE '%Manual%'
AND jacket LIKE '%Dragon';
```
When the index is created, the computer does funny magic on the specified column to optimise it for queries. So querying that column later on will take way less time.