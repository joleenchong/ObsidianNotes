A buffer is a memory area that stores data being transferred between 2 devices and an app.

Done for 3 reasons:
- cope with device speed mismatch - file downloading is slower than file uploading (e.g. modem to hard disk)
- cope with device transfer size mismatch
- maintain copy semantics - data written to disk must be version at time of app [[System call]], not most recent content of app's buffer if there are any changes

Think of youtube buffering when connection is too slow

Lecture 2 Slide 31