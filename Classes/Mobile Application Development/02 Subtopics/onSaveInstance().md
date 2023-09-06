Allows to save temporary UI state data in case activity is destroyed and recreated due to configuration changes (e.g. portrait to landscape mode) or system constraints (e.g. low memory).

Rotating screen example:
```Java
int i = 0;
private static final String COUNTER ="com.example.counter"

@Override
protected void onCreate(Bundle savedInstanceState)
{
	super.onCreate(savedInstanceState);
	setContentView(R.layout.activity_main);

	Button button = findViewById(R.id.button);
	TextView textView = findViewById(R.id.button);

	//retrieving data
	if(savedInstanceState!=null)
	{
		String value = savedInstanceState.getString(COUNTER);
		textView.setText(value);
	}

	button.setOnClickListener(new View.OnClickListener()
	{
		@Override
		public void onClick(View view)
		{
			i = i+1;
			textView.setText(String.valueOf(i));
		}
	});
}

//saving data
@Override
public void onSaveInstanceState(@NonNull Bundle outState)
{
	super.onSaveInstanceState(outState);
	outState.putString(COUNTER, textView.getText().toString());
}
```