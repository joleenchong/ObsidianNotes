Type safety - letting the compiler check data types for you

Generics allow you to reuse methods with type safety:
```java
// Non-generics:
public String getMatch(String[] arr, String val) {...}
public LocalTime getMatch(LocalTime[] arr, LocalTime val) {...}
// Generics:
public <T> T getMatch(T[] arr, T val) {...}
```
- T represents any type, but all Ts are the same

It's more common to use generic things than to create your own (e.g. built-in libraries).

To create generics:
```java
// Declare type parameters - like a mostly normal data type:
public class MyClass<S,T>
{
// conventionally type paras are 1 uppercase letter
	private S value;
	private List<T> list = new ArrayList<>();

	public MyClass(S value, T first)
	{
		this.value = value;
		this.list.add(first);
	}
	public S getValue()
	{
		return value;
	}
}
```
- Type para naming conventions:
	- E - element (e.g. lists / sets)
	- K, V - key and value (e.g. maps)
	- N - number
	- R - result
	- T - type, arbitrary default choices
	- S, U, V - arbitrary default choices following T
- Methods can declare type parameters too:
```java
public class ListUtils
{
	public <E> E getMiddle(List<E> list)
	{
		return list.get(list.size()/2);
	}
}
```

When compiler fails to infer a type:
```java
// Specify method type arguments:
someObj.<String, Integer>someMethod();
SomeClass.<LocalTime>someStaticMethod();
```

Erasure:
- compiler checks types to ensure type safety
- compiler erases any generics
- compiled code just has `Objects` instead of `T`

Generic limitations:
- no primitives - use classes instead (e.g. int, a primitive vs Integer, a class)
- no runtime checking cause erasure
	- no `if(T == String) {...}` or `if (list instanceof List<String> {...}` 
- no generic array creation - arrays MUST know their element type at runtime
	- can upcast to generic array type - `<T> void method(T[] array {...}`

Bounded type parameters - making generics more specific:
```java
// T must extend JComponent cause of show()
// MyClass<JButton> is valid, but NOT MyClass<String>
// Use extends for both classes and interfaces here
public class MyClass<T extends JComponent>
{
	private T component;

	public void show()
	{
		// T has method 'setVisible()' because JComponent does
		component.setVisible(true);
	}
}

// T can also extend multiple things (an intersection type)
public class Example<T extends thing1 & thing2> {...}
```

Wildcards:
- used if T needs no exact value (for using generic types)
- Types:
	- Unbounded
		- `List<?> a;`
		- any list
	- Upper-bounded / covariant
		- `List<? extends Abc> b;`
		- a list of some subclass of Abc / of Abc itself
		- used to get info from generic object
		- producer extends
	- Lower-bounded / contravariant
		- `List<? super Abc> c;`
		- a list of some superclass of Abc / of Abc itself
		- used to set / put info into generic object
		- consumer super