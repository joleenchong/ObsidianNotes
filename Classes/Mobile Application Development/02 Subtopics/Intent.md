A message object to request action, launch activities, and pass data across components.

Structure:
- component - name of activity to launch -> unspecified means implicit
- action - string label specifying what you want to do
- data - URL/URI for source of data 
- type - specifies data type (what does MIME mean)
- category - set of string labels to refine what you want to do
- extras - name-value pairs to pass other needed parameters

- **explicit intent** - specifies the target component to launch by mentioning the component's class name or action
```java
Intent explicitIntent = new Intent(context, TargetActivity.class);
explicitIntent.putExtra("key", "value"); //optional data
startActivity(explicitIntent);
```
- Context - an abstract class that provides info about current state and environment of app 

Starting activity within an activity:
```Java
@Override
protected void onCreate(Bundle savedInstanceState)
{
	super.onCreate(savedInstanceState);
	setContentView(R.layout.activity_main);
	Button button = findViewById(R.id.menuButton);
	button.setOnClickListener(new View.OnClickListener()
	{
		@Override
		public void onClick(View view)
		{
			startSavingStateActivity();
		}
	});
}

private void startSavingActivity()
{
	Intent intent = new Intent(this, SavingStateACtivity.class);
	startActivity(intent);
}
```

Activity to activity communication:
- to pass data to new activity, add "extras" to Intent object
```java
//Sending basic types
Intent intent = new Intent(CurrentActivity.this, TargetActivity.class);
intent.putExtra("key_string", "Hello world");
intent.putExtra("key_int", 42);
intent.putExtra("key_boolean", true);
startActivity(intent);

//Sending bundles
Intent intent = new Intent(CurrentActivity.this, TargetActivity.class);
Bundle bundle = new Bundle();
bundle.putString("key_string", "Hello, world");
bundle.putExtra("key_bundle", bundle);
startActivity(intent);

//Retrieving basic types
String stringValue = getIntent().getStringExtra("key_string");
int intValue = getIntent().getIntExtra("key_int", defaultValue);
boolean boolValue = getIntent.getBooleanExtra("key_boolean", defaultValue);

//Retrieving bundles
Bundle receivedBundle = getIntent().getBundleExtra("key_bundle");
String stringValue = receivedBundle.getString("key_string");
int intValue = receivedBundle.getInt("key_int");
```
-  it's better to have a global static final variable that's impossible to change rather than sharing data keys to avoid errors
