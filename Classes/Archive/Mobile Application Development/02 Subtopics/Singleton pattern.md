Ensures only one class instance exists -> can store and retrieve data consistently across different activities. It will contain: private constructor, private instance of itself, method to access that instance

Example:
```java
public class MyDataManager
{
	private static MyDataManager instance;
	private String title;
	private int counter;
	//Getters
	public static MyDataManager getInstance()
	{
		if ( instance == null )
		{
			instance = new MyDataManager();
		}
		return instance;
	}
	public String getTitle() { return title; }
	public int getCounter() { return counter; }
	//Setters
	public void setTitle( String title)
	{
		this.title = title;
	}
	public void setCounter(int counter)
	{
		this.counter = counter;
	}
}
```
- setting data in calling activity:
```java
singletonButton.setOnClickListener(new View.OnClickListener()
{
	@Override
	public void onClick(View view)
	{
		startActivityUsingSingleTon();
	}
});

private void startActivityUsingSingleTon()
{
	MyDataManager myDataManager = MyDataManager.getInstance();
	myDataManager.setTitle(title.getText().toString());
	myDataManager.setCounter(Integer.parseInt(counter.getText().toString()));
	Intent intent = new Intent(this, SavingStateActiity.class);
	startActivity(intent);
	
}
```
- getting data in target activity - calling function in onCreate() method
```java
private void updateViewWithSingleTon()
{
	MyDataManager myDataManager = MyDataManager.getInstance();
	titleView.setText(myDataManager.getTitle());
	i = myDataManager.getCounter();
	counterView.setText(String.valueOf(i))
}
```
Note: can lead to potential memory leaks -> must clean up data when data is no longer needed