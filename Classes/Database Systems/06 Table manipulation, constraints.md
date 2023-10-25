Subqueries - a query that is part of another query:
- types:
	- scalar
	- column / row
	- table

Scalar subqueries:
- examples on slide 10-12
- operators:
	- IN
	- ANY - syntax - $x = ANY(<relation)$ returns true if x equals at least one tuple in relation. = ca be replaced with any comparison operator
	- ALL
	- EXISTS - returns true only if <\relation> or only if subquery result is not empty

Correlated subqueries - a subquery that uses data from an outer select

UNION:
- result of each select must have same amount of columns
- corresponding entries of each select must be of compatible type

Inserting many tuples with subquery:
```MySQL
-- Example
INSERT INTO Cproj
SELECT * FROM Proj
WHERE SYSDATE > endate;
```
- this also applies for delete and update

Creating tables from subqueries:
```MySQL
-- Example
CREATE TABLE Deptmanager AS
	--subselect
	SELECT empno, lastname, firstname, edlevel, deptno, deptname, salary
	FROM Emp
	JOIN Dept ON mgrno = empno;
```

Referential integrity constraint policies:
- RESTRICT (default) - reject modification if referential integrity
- CASCADE - changes in referenced attributes are similarly made in foreign key
- SET-NULL - when value in referenced attribute is modified, corresponding foreign key value is set to NULL

CHECK constraint - it validates the data in an attribute depending on a condition?

Questions and notes:
- What are the advantages of using subqueries over JOINs?
	- it's easier to read and understand a query since it reads more like a comment
- <> means NOT?