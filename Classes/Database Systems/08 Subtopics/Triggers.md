Triggers check for a condition and specify what action is desired.
- can activate before and after:
	- inserting
	- updating
	- deleting
- AKA Event-Condition-Action (ECA) rules:
	- event - a modification to database
	- condition - a SQL Boolean expression
	- action - any SQL statements

Creating triggers:
```MySQL
CREATE TRIGGER <trigger_name>
	<trigger_time> <trigger_event>
	ON <tablename> FOR EACH ROW
	[trigger_order]
	<trigger_body> -- the actual statemends

-- not in actual syntax, just to clarify what to put into the variables above
trigger_time: { BEFORE | AFTER}
trigger_event: { INSERT | UPDATE | DELETE}
trigger_order: {FOLLOWS | PROCEDES} <other_trigger_name>
```

- row-level triggers - execute once for each modified tuple
- statement-level triggers - execute once for an SQL statement, number of modified tuples don't matter
	- not supported in MySQL
- default order of trigger activation is order of creation -> use trigger_order to change that
- use BEGIN...END statements to execute multiple statements in trigger_body

Can't use BEFORE triggers to convert values to to certain data type as value checks occur before trigger activation

Example:
```MySQL
CREATE TRIGGER before_emp_insert_total
	BEFORE INSERT ON Emp
	FOR EACH ROW
		SET @total = @total + NEW.salary;
```
- OLD and NEW accesses columns affected by trigger
	- INSERT can only use NEW
	- DELETE can only use OLD
	- UPDATE can do both

Use SIGNAL to return error in MySQL:
```MySQL
SIGNAL condition_value
	[SET signal_information_item]
	[, signal_information_item]

-- not in syntax
condition_vlaue: {
	SQLSTATE [VALUE] sqlstate_value| condition_name
}
```

List all triggers:
```MySQL
SHOW TRIGGERS [{FROM | IN} db_name]
	[LIKE 'pattern' | WHERE expression];
```

Drop triggers:
```MySQL
DROP TRIGGER [IF EXISTS] <trigger_name>;
```