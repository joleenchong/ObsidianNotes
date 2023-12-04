Java threads - performs tasks in parallel:
- create threads in 2 ways:
```java
//Extending Thread class
class MyThread extends Thread {
	public void run()
	{
		//thread logic goes here
	}
}

//starting thread
MyThread thread = new Mythread();
thread.start();
```
```java
//Implement Runnable interface
class MyRunnable implements Runnable {
	public void run()
	{
		//thread logic goes here
	}
}
//starting thread
Thread thread = new Thread(new MyRunnable());
thread.start();
```

Thread joining - wait for thread to finish before proceeding with main thread execution
```java
Thread thread = new Thread(new MyRunnable());
thread.start();
try {
	thread.join(); //wait fr thread to finish
} catch (InterruptedException e) {
	//handle interruption exception
}
```

Thread interruption - tells a thread to stop and terminate gracefully
```java
Thread thread = new Thread(new MyRunnable());
thread.start();
//after code stops
thread.interrupt(); //tell thread to stop
```

Runnable:
- more flexible as Java only supports single inheritance
- allows for better code reusability
- separates thread behaviour from thread management logic
- can pass shared resources to multiple threads easily

Extending thread:
- simpler
- less boilerplate
- limited inheritance
- harder to reuse

ViewModels can pass data between background thread and activity.

Using thread for API calls (ass2b):
- slide 13
