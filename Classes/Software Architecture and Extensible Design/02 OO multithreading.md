The basics are covered in [[03 Process Synchronisation]] and [[05 Deadlock]].

A thread is a mechanism for running code in parallel. A task is the code you want executed.

```java
//Creating the task
public class MyTask implements Runnable
{
	@Override
	public void run()
	{
		//some code
	}
}

//Running the task in new thread
MyTask myTask = new MyTask();
Thread myThread = new Thread(myTask, "thread-name");
myThread.start();
```
You can also extend Thread and override its run method, but it won't be done here -> helpful to keep tasks and threads distinct.

Implementing Runnable is a case of the [[Strategy pattern]], while extending Thread is a case of the [[Template method pattern]].

Alternatives to this:
- creating a class that defines its own task internally and runs it in a new thread
```java
public class Thing
{
	private Thread thread;
	public void start()
	{
		//Defining task as anonymous / inner class
		Runnable task = new Runnable()
		{
			@Override
			public void run()
			{
				//some code
			}
		};

		thread = new Thread(task, "thread-name");
		thread.start();
	}
}
```
- defining tasks with [[Lambda functions]]
```java
Runnable task = () ->
{
	//some code
}
thread = new Thread(task, "thread-name");
thread.start();
```
- defining tasks with method reference
```java
thread = new Thread(this::task, "thread-name");
thread.start();

private void task()
{
	//some code
}
```

Shared resources that are mutable cause the actual nightmares -> use thread-safe shared resources 
- uses atomic operations -> resource locks itself when accessed
- examples:
	- `AtomicInteger` class
	- `Collections.synchronizedList()'
- standard java classes aren't atomic by default -> more efficient -> don't need to lock and unlock all the time
- to create own atomic classes:
```java
private class Counter
{
	private Object mutex = new Object();
	private int i = 0;

	public int get()
	{
		synchronized(mutex)
		{
			return i;
		}
	}
	public void add()
	{
		synchronized(mutex)
		{
			i++;
		}
	}
	//As a modifier
	//will lock mutex for duration of method
	//not applicable if need to lock multiple indepedent resources
	public synchronized void add()
	{
		i++;
	}
}
```
`Synchronized` not only locks the resources but also tells compiler to synchronise the memory in which fields are stored.
You can use the `volatile` keyword to perform memory synchronisation without locking.

Thread responsibility:
- start 1 thread and provide much / all code this thread runs
- have set of public getters and setters to be called by different thread
- contain [[Mutex Locks]] and shared resources as private fields -> allow the 2 threads to communicate

Monitors:
- mutexes with 4 operations:
	- lock
	- wait
	- notify
	- unlock
```java
Object monitor = new Object();
synchronized(monitor)
{
	//do smth
	monitor.notify();
}

//the other thread
synchronized(monitor)
{
	monitor.wait();
	//do smth
}
```

To cancel a thread:
```java
private Thread thread = new Thread();
thread.interrupt();
```
- method sets interrupted state to true -> code inside thread must do 1 of 2 things:
	- call blocking method (e.g. `wait()`, `Thread.sleep()`)
	- check interrupted status directly with `Thread.interrupted()`

