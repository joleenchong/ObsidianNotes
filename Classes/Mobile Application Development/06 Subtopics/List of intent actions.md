Dialling phone:
```java
private void callButtonClicked()
{
	int phone = 123456;
	Uri uri = Uri.parse(String.format("tel:%d", phone))
	Intent intent = new Intent();
	//android displays dialer interface with specified phone number pre-filled but not immediately called
	intent.setAction(Intent.ACTION_DIAL);
	intent.setData(uri);
	startActivity(intent);
}
```

Showing location on map:
```Java
private void showMapLocation()
{
	double latitude = 32.22;
	double longitude = 43.22;
	Uri uri = Uri.parse(String.format("geo:%f,%f", latitude, longitude));
	Intent intent = new Intent();
	//open or view piece of data like file / URL using appropriate app / activity
	intent.setAction(Intent.ACTION_VIEW);
	intent.setData(uri);
	startActivity(intent);
}
```

Sending text:
```java
private void sendTextOnClick()
{
	int phone = 123456;
	String smsText = "Testing";
	Uri uri = Uri.parse(String.format("smsto:%d", phone));

	Intent intent = new Intent();
	//opens up device's default messaging app with pre-filled recipient info and optional message data
	intent.setACtion(Intent.ACTION_SENDTO);
	intent.setData(uri);
	intent.putExtra("sms_body", smsText);
	startActivity(intent);
}
```

