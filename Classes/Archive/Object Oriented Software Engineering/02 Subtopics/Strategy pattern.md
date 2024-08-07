![[Pasted image 20240317231714.png]]

When you have several algorithms to achieve similar goals, they get their own class but implement a common [[Interface (Object)|interface]]. This utilises [[Polymorphism]].

Each strategy class / object embodies an algorithm. All algos must fit the same interface -> same kind of input data and results. When using, the code will not know which algorithm is being used (that's why it's called abstract lol).

Example: a music player may use different strategies to load different audio formats, but will achieve the same results.
```java
public class AudioPlayer
{
	private Map<String, TrackLoader> loaders = ...;

	public void play(String file)
	{
		String extension = file.substring(file.lastIndexOf(".") + 1);
		TrackLoader tl = loaders.get(extension);
		if (tl == null)
		{
			throw new AudioException("Unrecognised format");
		}
		//invokes the loader polymorphically
		Track t = tl.load(file);
	}
}
```

Strategy object creation:
```java
private Map<String, TrackLoader> loaders = new HashMap<>();

//just have to call this some time before it's used
public void initLoaders()
{
	loaders.put("mp3", new MP3Loader());
	loaders.put("m4v", new M4VLoader());
	loaders.put("flac", new FlacLoader());
}
```