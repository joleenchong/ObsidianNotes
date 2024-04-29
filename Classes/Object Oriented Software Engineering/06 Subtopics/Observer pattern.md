![[Pasted image 20240429134728.png]]
Classes:
- subject - generates events and passes to observer
	- has list of observers + add/remove methods + method to notify registered observers
	- when event happens, all observers notified
	- do not own, control, or even know types of observers -> association relationship
- observer - handles events, have their own responsibilities
	- implement an Observer interface
	- may also be known as listeners (e.g. Java Swing)

Division of responsibilities:
![[Pasted image 20240429134808.png]]

In a [[Model-View-Controller Architecture]] context:
- models are subjects -> changes to model data are events
- views are observers -> notified to update display when model data changes

Other implementations of observers:
- inner class within subject class (can also be made in a method)
- anonymous classes
- [[Lambda functions]]

NOTE: do not use Java's built-in Observer / Observable classes - deprecated

Example code:
```java
//Subject class
public class SubjectClass 
{
	private List<Observer> observers = new ArrayList<>();
	public void addObserver(Observer obs)
	{
		observers.add(obs);
	}
	public void removeObserver(Observer obs)
	{
		observers.remove(obs);
	}
	//Calls all registered observers
	public void notifyObservers()
	{
		for (Observer obs : observers)
		{
			obs.update(...);
		}
	}
}

//Observer Interface + classes
public interface Observer
{
	void updateForEvent(EventInfo info);
}

public class ConcreteObs
{
	//various things...
	...
	//event handling
	@Override
	public void updateForEvent(EventInfo info)
	{
		//...
		//update() can also take no parameter, and instead use
		// EventInfo info  = subject.getInfo();
	}
}
```

