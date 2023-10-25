Internal storage:
- Files in internal storage for the app cannot be directly accessed by other apps for security.
- storage path would look like `/data/data/com.example.appName/`
- limited to available space on device's internal memory
- after uninstallation, all data stored in internal storage associated with app is auto deleted
- how to use:
	- determine data to save into file
	- specify file name
	- open `FileOutputStream` to make file and open output stream for writing data
	- write data to output stream
	- close output stream to release system resources
- Permissions - slide 6
- slide 7 for example

External storage:
- shared among all apps
- path can vary but usually `storage/emulated` /  `sdcard`
	- accessed through `Environment.getExternalStorageDirectory()`
- provides more storage space
- how to use:
	- determine data to save into file
	- specify file name
	- check external storage availability before saving file
	- request permission to read and write to external storage
	- open `FileOutputStream` to make file and open output stream for writing data
	- write data to output stream
	- close output stream to release system resources

Research for storage:
https://developer.android.com/training/data-storage

Cameras and FileProviders:
- Dealing with photos:
	- define `FileProvider` in AndroidManifest.xml
	- give `FileProvider` as Uri to camera app
	- give camera app permission to write to it
- revisit this for assignment 2A

Slide 29 for Pixabay

Slide 31 for URL