Types of errors:
- compiler errors
- platform errors - failure of runtime environments -> nothing much you can do
- internal (logic) errors
	- caused by bugs / defects
- external errors - expected situations
	- e.g. invalid input formats, network failures
	- app must respond to these - catch them

Exceptions:
- used to manage both internal and external errors
- main superclasses:
	- `Throwable` <- `Exception` <- `RuntimeException`
	- `Throwable` <- `Error`
- Throwable - superclass of everything that can participate in throwing and catching
- Error - represents platform errors, treat them like internal errors
- RuntimeException - mostly internal errors
- Exception, apart from RunTimeException - mostly external errors

Throw:
```java
throw new ExceptionType("Message");
```
- throws new exception object
- if not caught in current method, propagates to caller
- if not caught in caller, propagates to caller's caller
- if not caught at all, thread ends

Don't catch exception superclasses cause they don't help much for debugging.

Guard conditions:
- helps to fail fast
- don't catch them
```java
//IllegalArgumentException guard condition
public static int readInt(int min, int max, int defaultValue)
{
	//guard condition for nonsense inputs
	if(min > max) {throw new IllegalArgumentException(); }

	int value = new Scanner(System.in).nextInt();
	if(value < min || value > max)
	{
		value = defaultValue;
	}
	return value;
}

//IllegalStateException guard condition
public class StringCounter
{
	private List<String> list = new ArrayList<>();
	private Map<String,Integer> tally = null;
	
	public void add(String s)
	{
		//guarding against wrong state to do this
		if(tally != null) {throw new IllegalStateException();}
		list.add(s);
	}
	public void count()
	{
		if(tally != null) {throw new IllegalStateException();}
		tally = new HashMap<>();
		//counts all equivalent strings in list and stores count in tally
	}
	public int getCount()
	{
		if(tally==null) { throw new IllegalStateException();}
		return tally.get(s);
	}
}
```

Checked exceptions - forces you to either:
- catch in current method
- declare in throws clause -> puts same responsibility on caller

Responsibility for errors is a design choice -> one method can tell when something goes wrong but maybe only its caller can handle it

Defining own exceptions:
```java
public class NewException extends Exception
{
	public NewException(String msg)
	{
		super(msg);
	}
	public NewException(String msg, Throwable cause)
	{
		super(msg, cause);
	}
}

//to use, you need to throw
public Data doSomething() throws NewException
{
	if(...)
	{
		throw new NewException("Custom message");
	}
	return data;
}
```
- extend RunTimeException if want unchecked exception

Exception chaining - replacing one exception type with another:
```java
try {...}
catch(IOException | ParseException e)
{
	throw new ConfigException("Config could not be inited," e);
}
```
- divides responsibilities more clearly
- caller only deals with ConfigException, not other 2 -> more relevant
- passing the cause (e) to get a stack trace for entire history

Try-with-resources:
```java
private String readLine(String file) throws IOException
{
	try(BufferedReader br = new BufferedReader(new FileReader(file)))
	{
		return br.readLine();
	} //automatically calls br.close() when try ends
}
```
- br is the resource
```java
try {...}
finally
{
	//code here guaranteed to run
	//try and catch blocks end
	//if another exception happens here, it suppresses original exception
}
```

Logging:
- may not need to take action for every catch block -> do some logging instead
```java
import java.util.logging.Logger;
import java.util.logging.Level;

private static final Logger logger = Logger.getLogger(someClass.getName());
try{...}
catch(SomeException e)
{
	logger.log(Level.INFO,"SomeException in method()", e);
}
```
- more advanced form of print statements lol
	- stays in code permanently
	- log statements have severity level and automatic class name and time stamp
	- can be turned on/off at runtime
	- can output to different places
- assign a logger for each class in a private static final field -> all objects of same class share logger
- getLogger() makes logger take name & integrate new logger into log manager
```java
logger.log(Level.INFO, "Doing something");
logger.log(Level.WARNING, "Something is off");
logger.log(Level.SEVERE, "Big problem :O");

//simplifies above
logger.info();
logger.warning();
logger.severe();

//with embedded values using lambdas
logger.info(() -> "Getting " + name + " for things");
```
- [[Lambda functions]] avoids creating the string when logging turned off for performance
- log levels from lowest to highest:
	- FINEST
	- FINER
	- FINE
	- CONFIG
	- INFO
	- WARNING
	- SEVERE
- other log frameworks may have different sets of levels
- log messages can be filtered by level
- log handlers - choosing output methods:
	- ConsoleHandler - displays messages
	- FileHandler - appends to log file on disk
	- SocketHandler - sends over network
	- MemoryHandler - keeps log data in memory until triggering event then sends to other handlers
	- can config minimum log levels for handlers
- Config file - property files for logs and stuff
```
# Set global log level
.level = INFO

# Set log level for specific loggers
app.Main.Class = FINE
app.UI.OtherClass = WARNING

# Output to screen and to file
handlers = java.util.logging.ConsoleHandler, java.util.logging.FileHandler

# Config for console logging
java.util.logging.ConsoleHandler.level = WARNING
```
- no hard-coded filename -> set in the system properties in build.gradle or the -D flag from commandline