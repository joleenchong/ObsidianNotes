AKA contract.

The inheritance of a public method signature. They are the key to [[Polymorphism]]. It allows replacing classes with other classes that have the same interface. Declarations of interfaces can specify an interface without an implementation.

```java
public interface Shape
{
	//no implementation defined
	int getArea(); //implicitly public abstract
	int getPerimeter();
}

public class Square implements Shape
{
	@Override public int getArea() {
		//square-specific implementation
	}
	@Override public int getPerimeter() {...}
}
```

