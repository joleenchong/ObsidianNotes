Stored procedure - an object made with `CREATE PROCEDURE` and invoked using `CALL`.
- has no return value but can modify its parameters for later inspection by caller
- can generate result sets to return to client program

Stored function - an object made with `CREATE FUNCTION`; used like a function
- invoked in an expression
- returns value

Stored routine (procedure / function) - set of SQL statements that can be stored in server

Why?
- clients can refer to stored route instead of redoing individual statements
- useful in certain scenarios:
	- multiple client apps written in different languages or work  on different platforms, but need to do same database operations
	- when security is very important -> consistent and secure environment,  instead of giving access rights to users, can give them to stored routines

Defining procedure:
```MySQL
CREATE PROCEDURE <proc_name> ([<paremeter_list]>)
[COMMENT <quoted_string>]
<statement>;
```
Defining function:
```MySQL
CREATE FUNCTION <proc_name> (<[parameter_list]>) RETURNS <type>
[COMMENT <quoted_string>]
<statement>;
```
- proc_name - name of procedure
- [[Stored procedure parameters|parameter_list]] - arguments passed in which will usually be global variables
- RETURNS - indicates what type of value function will return
	- functions output exactly 1 value; parameters can output info through parameters
- COMMENTS - briefly describes procedure -> good practice, but not required
- statement - contains statements to execute within procedure / function

User-defined variables:
- persists for the entire session
- starting new session means all previous user-defined variables are lost
- can't use variables to store info persistently -> only for communication
- use `DECLARE` to define local variables
- defining:
	- `SET @<var_name> = <expression?` -> persists outside of procedure -> stays in memory and can be passed outside of procedure
		- types can't be specified
	- `DECLARE <var_name> <type> [DEFAULT <value>]` -> local: only valid within compound statement that is declared
	- `SELECT... INTO <variable list>` -> results can be retried into variable lists using this
- variable names start with @, and can contain any letters + numbers + . + _ + $

Flow control statements - loops and if else:
-  can be used in compound statements
```MySQL
IF <condition> THEN
	<statement(s)>
	ELSEIF <condition>
	<statement(s)>
	ELSE
	<statement(s)>
END IF;

[<label>] LOOP
	<statement list>
	LEAVE [<label>]; /* Put this in a if statement so that you can get out */
END LOOP [<label>];
```

Cursors:
- an identifier or pointer to specific row of query result -> used to traverse over set of rows of tables of database
- can be used with loops
- when declaring, associate it with a select statement that retrieves rows for cursor to traverse
- cursors must be opened to be used
```MySQL
/*Declaring*/
DECLARE <name> CURSOR FOR <select>;
/*Opening*/
OPEN <name>;
/*Fetching*/
FETCH <name< INTO <var_list>;
/*Closing*/
CLOSE <name>;
/*Handler for dealing with No Data condition - no more rows*/
DECLARE CONTINUE HANDLER FOR NOT FOUND SET <name> = TRUE;
```

Examples:
- without parameters
```MySQL
CREATE PROCEDURE resetEmpBonus()
	COMMENT 'Sets bonus field to zero for all employees in table'
	UPDATE Emp
		 SET bonus = 0;
-- Execution
CALL resetEmpBonus();
```
- with parameters
```MySQL
CREATE PROCEDURE resetEmpBonus2(
	IN val DECIMAL(8,2)
)
	COMMENT 'Set bonus fields to a value provided by management for all employees in Emp table'
	UPDATE Emp
		SET bonus = val;
-- Execution
CALL resetEmpBonus2(100);
```

```MySQL
CREATE PROCEDURE insNewEmp(
	eno CHAR(6),
	fname VARCHAR(12),
	minit CHAR(1),
	lname VARCHAR(15),
	wdept CHAR(3)
)
COMMENT 'Inserts new employee into table'
INSERT INTO Emp(empno, firstname,midinit, lastname, workdept, bonus)
VALUES (eno,fname,minit,lname,wdept,0);
-- Execution
CALL insNewEmp('100001', 'Lin', 'M', 'Soon', 'B01');
```
- compound statements:
```MySQL
DELIMITER //
CREATE PROCEDURE resetEmpBonus()
	 COMMENT 'Sets bonus field to 100 for employees assigned to department A00, 50 to all others'
	BEGIN
		 UPDATE Emp SET bonus = 100 WHERE workdept = 'A00';
		 UPDATE Emp SET bonus = 50 WHERE workdept <> 'A00';
	END
	//

DELIMITER ;
```
- DELIMITER makes it so that the MySQL statement doesn't execute immediately on encountering semicolon
- local variables:
```MySQL
DELIMITER //
CREATE PROCEDURE insNewEmp (
	fname VARCHAR(12),
	minit CHAR(1),
	lname VARCHAR(15),
	wdept CHAR(3)
)
COMMENT 'Insert new employee into table Emp'
BEGIN
	DECLARE nextid CHAR(6);
	SELECT MAX(empno) + 1 FROM Emp INTO nextid; /*you could just use AUTO_INCREMENT*/
	INSERT INTO Emp(empno, firstname, midinit, lastname, workdept)
		VALUES (nextid, fname, minit, lname, wdept);
END
//
DELIMITER ;
```
- cursors:
```MySQL
DELIMITER $$
CREATE PROCEDURE createProgList (OUT pList varchar(2000))
BEGIN
	DECLARE done INTEGER DEFAULT 0;
	DECLARE fullName varchar(40) DEFAULT '';
	COMMENT 'Declare cursor for getting first name and last name of employees with job title programmer'
	DECLARE curProgNames CURSOR FOR SELECT CONCAT(firstname, '', lastname) FROM Emp WHERE job = 'Programmer';
	COMMENT 'Declare NOT FOUND handler'
	DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;

	OPEN curProgNames;
	getProgNames: LOOP
	FETCH curProgNames INTO fullname;
		IF done = 1 THEN
			LEAVE getProgNames;
		END IF;
		# creating full name list
		SET pList = CONCAT(pList, ', ', fullName);
	END LOOP getProgNames;
	CLOSE curProgNames;
END
$$
DELIMITER ;
CALL createProgList(@pList)
SELECT @pList;
```

Questions:
- When would you use a procedure and when would you use a function?