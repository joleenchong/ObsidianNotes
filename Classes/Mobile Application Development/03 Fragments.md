A fragment is a sub-controller for part of the UI in an [[02 Activities|activity]]. The activity decides which fragments it'll have. The layout reserves space for the fragment's mini UI (it may also occupy the whole screen)

Why?
- can reuse across different activities
	- consistent layout and logic
- flexible - a single activity can switch btwn fragments
	- fragment transaction - adding / replacing fragments

FrameLayout - a layout element that defines where to put a fragment
- in XML, starts off empty -> filled up at runtime when fragment is attached
- needs ID to find it at runtime
```XML
<FrameLayout
	android:id="@+id/f_container"
	.../>
```

Each fragment has own separate XML layout file and java file. In an activity, you can make multiple fragment objects.

FragmentManager - adds, removes, replaces, and shows fragments on screen:
- beginTransaction() - starts new transaction; use with add() to add fragment to container view
- replace() - replaces existing fragment with new one in container
- remove() - does what it says
- can re-create fragments if activity is destroyed & recreated
- keeps fragments in sync with activity lifecycle
Loading example:
```java
private void loadFragment()
{
	FragmentManager fm = getSupportFragmentManager();
	Fragment frag = fm.findFragmentbyId(R.id.f_container);
	if(frag==null)
	{
		fm.beginTransaction().add(R.id.f_container, fragment).commit();
	}
	else
	{
		fm.beginTransaction().replace(R.id.f_container, fragment).commit();
	}
}
```

Best practice:
- fragment view elements should be accessed within owner fragment (including event listeners)

Button click within fragment:
```java
public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstance State)
{
	View rootView = inflater.inflate(R.layout.fragment, container, false);
	Button changeButton = rootView.findViewById(R.id.changeButton);
	ViewGroup constraintLayout = rootView.findViewById(R.id.layout);

	changeButton.setOnClickListener(new View.OnClickListener()
	{
		@Override
		public void onClick(View view)
		{
			if (toggle==0)
			{
				constraintLayout.setBackgroundColor(Color.BLUE);
				toggle = 1;
			}
			else
			{
				constraintLayout.setBackgroundColor(Color.GREEN);
				toggle = 0;
			}
		}
	});
	return rootView;
}
```

LayoutInflater - takes a layout reference, reads XML of all View objects and creates UI based on it, then returns rootView object
- Parameters: 
	- resource ID for layout to inflate
	- parent view group to attach inflated view to (if null, the fragment is responsible for attaching view)
	- boolean for whether inflated view should be attached to parent view group (true to attach, false otherwise)

Communication between fragments / activities:
- LiveData - observable data holder class that is lifecycle-aware
	- observable - an observer is notified when data in LiveData object changes
	- lifecycle-aware - when attaching observer to LiveData, observer is associated with LifeCycleOwner (usually activity / fragment)
		- LiveData only updates observers that are in active lifecycle state like STARTED / RESUMED
- ViewModel - a component to store and manage UI-related data, survive configuration changes (e.g. screen changes), and avoid pitfalls like memory leaks
	- remains in memory until ViewModelStoreOwner it scopes to disappears -> occurs when activity finishes or fragment detaches
	- usually requested the first time system calls an activity object's [[onCreate()]] method -> exists from when first requested until activity is destroyed
![[Pasted image 20230821133232.png]]
- ViewModelProvider - helps create and manage ViewModels
	- Creating ViewModelProvider instance and getting ViewModel instance thru it
```java
MainActivityData mainActivityDataViewModel = new ViewModelProvider(this).get(MainActivity.this);
```

