One class can have many objects, which can form complex structures.

Object diagrams:
- shows object structure
- no methods
- have to specify values of objects at runtime
- objects aggregate / associate with other objects -> only one-one relationship
- objects don't inherit from others (those are classes)
![[Pasted image 20240322172223.png]]

If you need to give access to an object field:
- return a reference
- return a copy using `.clone()` method
- return a read-only wrapper

Wrapper classes:
- It 'wraps' around another class -> can access it, but not modify it
- Java has pre-defined wrappers for lists, sets, and maps, use `Collections.unmodified<object>(objectName);`
```java
//Example
public class ReadOnlyPoint
{
	private Point p;
	public ReadOnlyPoint(Point p) { this.p = p; }
	public int getX() { return p.getX(); }
	public int getY() { return p.getY(); }
}
```

Copy / wrap an object if it's mutable and part of the internal workings of another class.

Law of Demeter - objects should only communicated if they were directly aggregated / associated
- avoid chains of getter class
- avoid coupling between distant classes
- may create clutter in intermediate classes

Patterns:
- [[Decorator pattern]]
- [[Composite pattern]]
