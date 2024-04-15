Basically breaking things down into smaller things.

[[Model-View-Controller Architecture]]

Packages and namespaces - a grouping of classes:
- Packages for UML, Java, Python; namespaces for C++ and C#
- form compile-time hierarchy -> irrelevant at runtime
- good to organise code
- avoids naming conflicts -> can assign any name without conflicting with existing ones
![[Pasted image 20240408090151.png]]

Package declaration in Java:
```java
package edu.curtin.app;
import ...;

public class App{...}
```
- must name all proper Java apps -> unnamed are for experimentation
- package names have more than 1 part separated by dots '.' -> reflect hierarchy
- names should start with reversed domain name with labels for structural parts of app

Package encapsulation:
- if public, protected, and private omitted, classes and interfaces are package-private -> only visible within package
- helps separate a package out 

Don't create nested classes unless inside class is conceptually part of outer class.