References - a special value that points to an object
- makes [[Polymorphism|polymorphism]] possible -> can write generalised code that doesn't need to know exact datatype it's using -> improves reuse and reduce coupling
- cannot work with value types (primitives)

Upcasting - converting from subclass reference to superclass one
- e.g. Employee is a subclass of Person
```Java
Employee emp = new Employee();
Person p = emp; //upcasting from Employee to Person
```
- used when method return types are more specific
- or when return type is more general than return value
- Upcasting List objects can have some confusion
```Java
//Upcasting main type
LinkedList<Person> linked = new LinkedList<>();
List<Person> list = linked //LinkedList -> List
Object o = linked // LinkedList -> Object

//Cannot upcast element type
List<Employee> empList = ...;
List<Person> pList = empList; //will throw error as List<Employee> is not type of List<Person>
```
- to deal with above, can use the following:
```Java
List<? extends Person> pList = ...; //wildcard -> some type that extends Person
List<Employee> emps = ...;

pList = emps;
```

Downcasting - converting a general reference back to a more specific one
```Java
Employee emp = (Employee)person;
```
- often a bad idea -> better to stick with same reference type and avoid casting altogether
- can be used for equals() method for verification

Subclasses inherit 2 things from superclass:
- [[Interface (Object)]] (AKA Contract) - all public method signatures
- [[Implementation (Object)]] - all code & private methods

Patterns:
- [[Strategy pattern]]
- [[Template method pattern]]

