Software architecture is the set of high-level design choices made to fulfil various non-functional requirements.

Structural separation of an application:
- not just classes / interfaces, much broader
- in local apps:
	- app can be divided into different processes
		- each process has separate memory & is treated as independent thing by OS -> must communicate through IPC
	- several distinct components running within single process -> components share memory -> can interact thru method / function calls
- in distributed apps:
	- consequences of splitting system this way:
		- speed -> much slower as it travels across networks
		- complexity -> communication btwn components more complex due to need to serialise and deserialise data
		- security
		- components are swappable to some extent if communication is kept reasonably simple

Cross-platform / platform-independent apps:
- app can run on any device
- difficult due to difference in APIs
- if you write 1 version of the app for a process VM (e.g. JVM, .NET, CPython), it can run on all OSes that VM can run on:
	- process VMs differ from system VMs like VMware and Virtual Box -> only runs 1 app at a time and is more like a special software-based CPU
- how to approach:
	- make just the byte code available to users -> users need to have relevant VM software -> packaging more lightweight cause only need to make 1 thing
	- package byte code and VM in self contained form -> still need to provide different platform-specific download options
	- get build system to compile byte code to platform-specific machine code to make different platform-specific versions -> not actually running on VM but still uses lots of the same supporting infrastructure
- VMs don't completely solve platform independence -> different UIs btwn desktop UIs and mobile UIs
- VMs may not always be the right choice:
	- if absolute best possible performance is mission critical, may need to write native code from start
	- if the thing you're making is a VM or web browser, you can't have it running on another VM and on another VM
![[Pasted image 20240719002213.png]]
- kinda like the [[Strategy pattern]]

Frameworks:
- like libraries / APIs, but defines how app will be structured
- takes care of tedious stuff so you can focus on core functionality
- provide overarching inheritance hierarchy & event handling system -> parts of app expected to extend parts of framework
- define what component parts of app are / what type of things your app can be made of (e.g. Model-View-Controller structure)
- often specify naming & organising conventions
- sometimes provide a build system for compiling app

Plugins and scriptability:
- a way to future-proof app by making it more extendable
- plugins - tend to be lower level mechanism where third-party code is written in same / similar language to original app -> completely unconstrained by app and can make directly make calls to the OS
- scripts - tend to be higher-level and run by an interpreter embedded in app -> app can constrain what scripts can do in theory since it controls interpreter
- must create local APIs (different from web APIs) for plugins and script to interact with app
- significant security challenges:
	- scripts could be sandboxed so they don't have access to other parts of platform -> not guaranteed
	- not possible for plugins
	- could have centralised distribution system with human-based verification scheme -> added ongoing cost

Multithreading:
- helps achieve performance requirements by using multiple CPU cores at same time
- can schedule CPU-intensive tasks to run alongside IO tasks
- UI can remain operational while long-running task is performed in background

