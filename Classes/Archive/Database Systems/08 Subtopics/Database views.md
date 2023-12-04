A table derived from other stored tables (base / defining table)   -> basically a stored query
- two kinds:
	- virtual - not stored in database, just a query
	- materialised - actually constructed and stored -> not supported in MySQL
- triggers can't be associate with views
- queries can be used like base tables

Creating:
```MYSQL
CREATE VIEW view_name [(column_list)] AS

-- to replace
REPLACE VIEW ....
```

Dropping:
```MYSQL
DROP VIEW [IF EXISTS]
	view_name;
```

Example:
```mysql
CREATE VIEW LocalStudents AS
SELECT studentID, firstname, Students.courseID AS course
FROM Students INNER JOIN Courses ON
country = 'Australia' AND Students.courseID=Courses.courseID;
```

Usage:
- hide query complexity
- limit access to sensitive tables
- make consistent business rules

Tuple modification:
- there must be one-to-one relationship between rows in view and underlying table to update a table
- view should contain all columns of base table that don't have default value
- joins, subqueries, aggregate functions are not possible to update in Views

Limitations:
- performance
- update restrictions