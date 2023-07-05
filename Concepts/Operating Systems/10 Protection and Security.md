Chapter 14 & 15 of OS textbook

--------

Protection domains:
- principles:
	- least privilege - processes / user / system given just privileges to perform tasks
	- need to know - process should access only resources to complete its task
- protection domain - a collection of [[access rights]]
- association of a process and domain can be:
	- static - set of resources available to process is fixed through process lifetime
	- dynamic - set of resources can change
		- this allows to keep minimum access rights

Access matrix and implementation:
[[access matrix||Access matrix]]

Security problems:
- CIA - Confidentiality, Integrity, Availability
	- Confidentiality - unauthorised reading of data
	- Integrity - unauthorised modification of data
	- Availability - unauthorised destruction of data
- Methods to breach security:
	- masquerading - pretend to be someone else
	- replay attack - repeat valid data transmission for malicious purpose
	- man in the middle - masquerade as legit sender to legit receiver & vice versa
	- session hijacking - intercept communication session

