Outline:
- layouts
- drawable
- different layouts
- guideline
----------------
Layouts:
- GUIS are hierarchical
- Views - buttons, EditText, ViewText, etc.
	- ViewGroup - a View that contains other views
- Container elements - rectangles that fence in child elements
- x1, y1, x2, y2 not fixed at compile time -> calculated when GUI is displayed
- LinearLayout - container that arranges elements in a line
	- can be nested
	- size and padding adjusted to fit available space
- ConstraintLayout - container that places elements relative to each other based on specified constraints
- Density-independent Pixels (dp) - unit of measurement to express distances, dimensions, sizes
	- formula to convert dp to px:
$$ px = dp \times (dpi/160)$$
LinearLayout:
- android:layout_width & android:layout_height - important for positioning and sizing views correctly
	- Values:
		- match_parent - makes view fill parent's width/height
			- expands to take all available space
		- wrap_content - makes view size fit to content
		- specific_size - a specified size
		- 0dp/px - allows for using constraints in ConstraintLayout
- android:gravity - control alignment of View's content inside View itself
- adroid:layout_gravity - control alignment of View within parent container

ConstraintLayout:
- each view inside has 1 or more constraints to define position relative to smth else

To find default UI layout (XML) - app/src/main/res/layout/
To find alternate UI layouts - app/src/main/res/layout-qualifier/

Drawables - graphic resources to define visual elements for various UI components & backgrounds
- bitmap drawables - raster images. stored in res/drawable dir
- vector drawables - XML-based graphics. stored in res/drawable dir with .xml extension
- shape drawables - XML-based graphics to define simple shapes for making backgrounds / simple icons. stored in res/drawables with .xml extension
- To add - copy image directly to directory
ImageView & ImageButton:
```XML
<ImageView android:id="@id/imageView"
...
app:srcCompat="@drawable/image_name" />
```

Shapes:
- Round_button.xml:
```XML
<shape xmlns:android="https://schemas.android.com/apk/res/android"
	   android:shape="oval">
<solid android:color="@color/black"/>
<size android:width="200dp" android:height="200dp"/>
</shape>
```
