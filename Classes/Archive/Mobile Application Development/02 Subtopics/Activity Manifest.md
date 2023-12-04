Contains essential info on app. All activities must be declared in this file
```XML
<activity
		  android:name=".MainActivity"
		  android:label="@string/app_name"
		  android:theme="@style/AppTheme.NoActionBar">
	<intent-filter>
		<action android:name="android.intent.action.MAIN" />
		<category android:name="android.intent.category.LAUNCHER" />
	</intent-filter>
</activity>
```
- activity in intent-filter specifies this activity as the main entry point for the app