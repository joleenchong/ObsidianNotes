A method or class entirely for making objects -> chooses between subclasses so no one else has to.

Factory method:
- calls constructors -> separates / decouples code that uses new object from class being created
- removes hard-coded dependencies
- when made in superclass, acts like polymorphic constructor
	- not allowed in java for interfaces
- kinda just put them in their own class -> don't belong anywhere else

Example code:
```java
public static MediaLoader makeLoader(String file)
{ // Factory
	MediaLoader loader = null;
	if(file.endsWith(".mp3") || file.endsWith(".flac"))
	{
		loader = new AudioFileLoader();
	}
	else if(file.endsWith(".mp4") || file.endsWith(".avi"))
	{
		loader = new VideoFileLoader();
	}
	return loader;
}
```