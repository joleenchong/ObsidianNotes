Kotlin:
- NULL safety!!!!
```Kotlin
val PI: int = 3.14
val isEasy: boolean = true
```
- declare variables with `val`, `: <data_type>` to assign type to variable, `= <value>` to put value into variable
- note: values in `val` do not change, but values in `var` do
- Functions:
```Kotlin
fun main()
{
	println("Hello World")
}

//with parameters
fun sum(a: Int, b: Int): Int //<-- return type of this fun
{
	return a + b;
}
```
- Lists (AKA arrays):
```Kotlin
val items = listOf("apple", "banana", "kiwifruit")
for (item in items)
{
	println(item)
}
```
- If else:
```Kotlin
fun maxOf(a: Int, b: Int): Int
{
	if (a>b)
	{
		return 0
	}
	else
	{
		return b
	}
}
//single line
fun maxOf(a: Int, b: Int) = if (a>b) a else b
```
- When blocks:
```Kotlin
fun describe(obj: Any): String  =
	when (obj) {
		1 -> "One"
		"Hello" -> "Greeting"
		is Long -> "Long"
		!is String -> "Not a string"
		else -> "Unknown"
	}
```
- Coroutine (like threads but better)
	- more lightweight
	- easier to use
	- can be given lifecycles
```Gradle
dependencies {
	implementation("org.jetbrains.kotlinx-coroutines-android:1.3.9")
}
```
```Kotlin
suspend fun urgentMessage(importantMessage: String)
{
	println(importantMessage)
}
viewModelScope.launch
{
	urgentMessage("Hey")
}
```

Jetpack Compose:
- a declarative UI framework -> will update itself to match an application's state -> vs XML (imperative ) -> makes prototypes and models then tries to fill them out
- Composables - a function that generates part of UI:
```Kotlin
@Composable
fun Greeting(name: String)
{
	Text("Hello $name")
}
```
- Layouts:
```Kotlin
@Composable
fun AristCardColumn()
{
	Column 
	{
		Text("Karen Aijo")
		Text("3 minutes ago")
	}
}

@Composable
fun ArtistCardRow (artist: Artist)
{
	Row(verticalAlignment = Alignment.CenterVertically)
	{
		Image(bitmap = artist.image, contentDescription = "Artist image")
		Column
		{
			Text(artist.name)
			Text(artist.lastSeenOnline)
		}
	}
}
```
- Modifiers and fields - parameters for changing composable appearances and stuff:
```Kotlin
private fun Greeting(name: String)
{
	Column(modifier = Modifier.padding(24.dp))
	{
		Text(text = "Hello,", color = Color.Green)
		Text(text = name)
	}
}
```
- States:
```Kotlin
@Composable
fun TextFieldSample()
{
	//This line will remember variable even when recomposed
	var text by remember { mutableStateOf("Hello")}
	TextField (
		value = text,
		onValueChange = { text = it}
		label = { Text("Label") }
	)
}
```
- any state needed for a task should be in its retrospective viewmodel
- recomposed - when jetpack reloads a part of UI
- state hoisting - keep state to higher level for other composables
- Lazy Layouts - recycler views but ez:
```Kotlin
@Composable
fun RecMessageList(messages: List<Message>)
{
	LazyColumn
	{
		items(messages) { message -> MessageRow(message) }
	}
}
```
- Scaffolds - a framework for more complex layouts
```Kotlin
fun HomeScreen(viewmodel: PicPickerViewModel)
{
	Scaffold (
		topBar = { TitleBar() },
		floatingActionButton = { AddButton(viewmodel = viewmodel) }
	) { innerPadding ->
		Column (
			modifier = Modifier
				.padding(innerPadding)
				.fillMaxSize(),
			horizontalAlignment = Alignment.CenterHorizontally
		) {
			LazyHorizontalGrid (
				rows = GridCells.Fixed(2)
			){
				itemsIndexed(viewmodel.imageList) 
				{ index, item -> 
					ImageCard(viewmodel = viewmodel, pos = index, bitmap = item)
				}
			}
		}
	}
}
```