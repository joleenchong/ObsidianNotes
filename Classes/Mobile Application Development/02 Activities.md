Activities - a single screen with a user interface:
- define layout through XML
	- stored in res/layout
- an activity must have a defined Java/Kotlin file that extends AppCompatActivity
	- handles activity logic and behaviour
- activities go through different states in lifecycle - done through callback methods

[[Activity Manifest]]
Activity lifecycle:
![[Pasted image 20230820153650.png]]

Callback methods:
- [[onCreate()]]
- [[onSaveInstance()]] 

Passing data across activities:
- [[Intent]] - a message object to request action, launch activities, and pass data across components
- Bundle - a collection of key-value pairs to pass data across components.
```Java
Bundle bundle = new Bundle();
bundle.putString("key_string", "Hello world");
bundle.putInt("key_int", 42);
bundle.putBoolean("key_bool", true);
```
- [[Singleton pattern]]

Sending back results:
- Result components:
	- result code - an integer constant of either `RESULT_OK` / `RESULT_CANCELLED`
	- intent object containing "extras" data
- [[ActivityResultLauncher]]
