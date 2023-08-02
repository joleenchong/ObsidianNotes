Key constraint - in a set of attributes, each value must be unique and not contain a null value (e.g. ID number)

Data manipulation: based on relational algebra
- Operations:
	- union, intersection difference
	- selection - eliminates some rows
	- projection - eliminates some columns
	- combine tuples from 2 relations
		- cartesian product - combines all tuples of 2 relations in all possible ways
		- join - selectively combine tuples of 2 relations
	- rename - affects relation schema

Functions:
- ROUND (n, m) - n is number to be rounded, m is places to the right of decimal point
- TRUNCATE (n,m) - n is number to truncate, m is places to right of decimal point
	- m can be negative -> becomes left of decimal point
- CONCAT(n...) - n is list of names to put together
```SQL
SELECT
	CONCAT(firstname, ' ', lastname) AS fullname,
	salary
FROM
	Emp;
```
- Date functions:
	- SYSDATE(), CURDATE(), CURTIME() - current date and or time
	- DATEDIFF, PERIOD_DIFF, SUBTIME, TIMEDIFF - difference btwn dates or times
	- DATE_FORMAT - overrides default date, search online for options format

Questions:
- During practical 1, it was pointed out that changed values do not update across the databases. Will there be a method that covers that later? I tried JOIN but it seemed to be more of a querying thing.