Inheriting code and private fields / methods from a superclass. Mainly about reusing common code from a superclass in each subclass.

```java
public class Person
{
	private String name;
	private int age;
	public void goOnHolidays() 
	{
		...
	}
}

public class Employee extends Person
{
	//will have name, age, and goOnHolidays() code
}

public class Customer extends Person
{
	//same as above
}
```

