On creation, the activity enters the created state. Used for basic app startup logic that happens only once in the activity's life cycle. The parameter `savedInstanceState` contains activity's previously saved state. If it has never existed before, it will be null.

```Java
public class MainActivity extends AppCompatActivity
{
	@Override
	protected void onCreate(Bundle savedInstanceState)
	{
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		
		//Additional code...
	}
}
```