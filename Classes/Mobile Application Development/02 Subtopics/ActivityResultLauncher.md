ActivityResultLauncher manages process of starting activity for a result and receives data once activity finishes.

- registerForActivityResult() - takes ActivityResultContract & ActivityResultCallback and results ActivityResultLauncher to launch other activity
- ActivityResultContract - provides set of pre-defined contract classes defining input and output types for common operations:
	- StartActivityForResult - for starting activities and receiving results. Input -> Intent, Output -> ActivityResult
	- RequestPermission - Input ->permission name, Output -> boolean (permission granted or not)
	- TakePicture - takes pictures using device's camera. Input -> none, Output -> URL representing captured image
	- GetContent -> gets content like image / document from external sources. Input -> content type, Output -> URL representing selected content

Steps for starting another activity for result:
- define ActivityResultLauncher with callback to handle result
```Java
String name ="";

ActivityResultLauncher<Intent> detailActivityLauncher = registerForActivityResult(
	new ActivityResultContracts.StartActivityForResult(),
	result ->
	{
		if (result.getResultCode()==RESULT_OK)
		{
			Intent intent = result.getData();
			name = intent.getStringExtra("name");
			detailActivityChecked = 1;
			printButton.setAlpha(1.0f);
			printButton.setEnabled(true);
		}
	}
);
```
- use ActivityResultLauncher to call target activity
```Java
detailButton.setOnClickListener(new View.OnClickListener()
{
	@Override
	public void onClick(View view)
	{
		Intent intent = new Intent(MainActivity.this, DetailActivity.class);
		detailActivityLauncher.launch(intent);
	}
});
```
- after activity is done doing things, can call setResult() to send back result to calling activity
```java
backButton.setOnClickListener(new View.OnClickListener()
{
	@Override
	public void onClick(View view)
	{
		Intent intent = new Intent();
		intent.putExtra("NAME", nameEditText.getText().toString());
		setResult(RESULT_OK, intent);
		finish();
	}
});

//actvity can also finish without result
public void finishWithoutResult()
{
	setResult(RESULT_CANCELED);
	finish();
}
```