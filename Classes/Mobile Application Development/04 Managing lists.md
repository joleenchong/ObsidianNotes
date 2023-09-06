RecyclerView:
- efficiently displays large sets of data
- dynamically creates elements when needed
- when item scrolls off, the view is reused for new items scrolling onscreen
- improves performance, app responsiveness, power consumption
Classes:
- RecyclerView - ViewGroup that contains views corresponding to data
- RecyclerView.ViewHolder - defines each individual element in list. on creation, doesn't have any data associated with it -> RecyclerView binds it to data after creation
- RecyclerView.Adapter - requests and binds views to data
- LayoutManager - arranges individual elements in list

![[Pasted image 20230824120545.png]]

Steps:
- add RecyclerView to dependencies - open build.gradle file and add
```gradle
dependencies {
	implementation'com.google.android.material:material:1.5.0'
	implementation 'androidx.recyclerview:recyclerview:1.2.1'
}
```
- define data structure for list items in cell
```java
public class MyData
{
	private String name;
	private String phoneNumber;
	public MyData(String name, String phoneNumber)
	{
		this.name = name;
		this.phoneNumber = phoneNumber;
	}

	public String getPhoneNumber() { return phoneNumber;}
	public String getName() { return name; }

	public void setPhoneNumber() { return this.phoneNumber = phoneNumber; }
	public void setName(String name) { this.name = name; }
}
```
- create XML layout for list items in cell
- create ViewHolder - MyDataVH.java
- create adapter - MyDataAdapter.java
- start by referencing list of data that will be scrollable
- implement onCreateViewHolder()
- implement onBindViewHolder()
- implement getItemCount()
- setup RecyclerView in activity's layout
- add data in MainActivity.java
- create view in MainActivity.java