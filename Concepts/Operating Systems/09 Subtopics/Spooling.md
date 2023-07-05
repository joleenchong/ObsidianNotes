A spool is a [[Buffering||buffer]] that holds output for a device (e.g. printer) that cannot accept interleaved data stream.
- each app's output is spooled to separate disk file
- when app finishes printing, spooling system queues corresponding spool file for output to printer
The OS provides control interface for users and system admins to display the queue, remove unwanted jobs, suspend printing, etc.