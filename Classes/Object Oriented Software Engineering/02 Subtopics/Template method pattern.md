An abstract class containing:
- template method - non-abstract method containing an algo
- hook methods - abstract methods called by the template method
	- abstract because superclass don't know how to do the action
	- protected because not part of superclass's contract to rest of system (unless hook method is useful by itself)
So it's like getting a bowl at Guzman's and choosing what toppings to give it.

This pattern is used for algorithms that are very similar except for some specific steps.

Code:
```java
public abstract class SuperClass
{
	public void templateMethod()
	{
		if (...)
		{
			hook1();
		}
		while (...)
		{
			hook2();
		}
		hook3();
	}
}

protected abstract void hook1();
protected abstract void hook2();
protected abstract void hook3();
}

public class SubClass extends SuperClass
{
	@Override protected void hook1() {...}
	@Override protected void hook2() {...}
	@Override protected void hook3() {...}
}
```

