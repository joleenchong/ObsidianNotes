JOIN variations:
- comma JOIN
	- not allowed - best to explicitly state type of join
```SQL
SELECT * FROM Students, Courses;
```
- NATURAL JOIN
	- joining two relations through common names - the natural way to join talbes
	- uses default constraint that attributes with same name must be equal
	- more efficient than theta / inner equi join. but condition isn't made explicit
	- when used with LEFT / RIGHT keywords, obtain all tuples from one side of relation and only tuples from other relation with same attribute values as that relation
- THETA JOIN
	- joins by using ON keyword to specify search condition
	- when search condition is ' = ', theta join is called Equi JOIN
```SQL
SELECT * FROM Students JOIN Courses ON Students.courseID = Courses.courseID;
```
- CROSS JOIN
	- simplest join to use
```SQL
SELECT * FROM Student CROSS JOIN Courses;
```
- INNER JOIN - it just distinguishes the join from other forms
	- Theta and Equi JOIN are this
- OUTER JOIN
	- for tables R and S, if tuple of R has no tuple of S to join, it's considered *dangling*
	- this join preserves dangling tuples by padding them with NULL
	- left and right outer join preserves dangling tuples of left and right table respectively
![[Pasted image 20230822150842.png]]
![[Pasted image 20230822161251.png]]
![[Pasted image 20230822161306.png]]
So my understanding is that selecting with an outer join will return every tuple on one table without the values of the other.

![[Pasted image 20230822161407.png]]

Sorting:
```SQL
SELECT <attributes>
	FROM <table>
	WHERE <condition>
	ORDER BY <attributes> [DESC];
```
- default is by ascending order, include DESC to reverse

GROUP BY - for aggregation in query:
```SQL
SELECT job, MIN(salary), bonus
FROM Employees
GROUP BY job;
```
- aggregation functions:
	- MAX
	- MIN
	- SUM
	- COUNT
	- AVG
- grouped attributes are automatically sorted -> can be turned off by adding `ORDER BY NULL;`
	- `GROUP BY <attribute> DESC;` reverses order
- if you want to use a where condition together with GROUP BY, must use HAVING
```MySQL
SELECT * FROM database
GROUP BY attribute
HAVING number > 4
```
