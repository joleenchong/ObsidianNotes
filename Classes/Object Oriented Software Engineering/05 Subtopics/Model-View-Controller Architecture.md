TODO: connect this to MAD notes, Django too?

An architectural pattern often used in user-interactive software. Apps are divided into:
- Model - stores and represents info
	- often just have getters and setters
	- connects to database
	- no business knowing abt views or controllers
	- meant to be used by other components
- Views - display UI and accept user input
	- arranged in a hierarchy (e.g. windows have toolbars and panels, toolbars have buttons and lists, etc.)
		- often forms a [[Composite pattern]] tree
	- usually predefined in GUI library -> can define own if needed
	- physical appearance defined in XML file
	- objects must:
		- display info from model (read-only access needed)
		- notify controller of user input
		- change self at controller's request
- Controllers - manage overall user interaction
	- start when event occurs (e.g. user input)
	- if user edits smth, will update model
	- if user requests info, will update view
	- needs:
		- read-write access to model
		- user input from view
		- to use views to request more info from user
	- each controller control separate part of UI

![[Pasted image 20240408084006.png]]

