Components:
- a set of functions that work together
- smallest chunk of app that can be moved to remote server
- the interface for external clients and links with app dynamically via OS
- prefabrication?
- defined by interface it exposes to external clients

Components represent the services a server can perform while objects represent things in a simulated system -> but [[REST API|REST]] blurs this significantly -> services that produce and consume objects

| Objects                                 | Components                               |
| --------------------------------------- | ---------------------------------------- |
| represents things in a simulated system | represents services a server can perform |
| technically specific                    | architecturally specific                 |
| internal -> only seen by other objects  | exposed to other apps                    |
| compile time linking                    | run time linking                         |
| implementation is specific and reusable | implementation details are obtuse        |

Service Oriented Architecture:
- services - components that clients connect to to execute task
	- cannot be passed around (clients have to go to them
- prevents distribution -> chunks off sets of objects by defining distinct siloed behaviours thru groups of components

Common Object Request Broker Architecture (CORBA):
- Object Request Brokers (ORBs) - middleware service that allow languages to communicate over network -> cross-compatible
	- represented as objects -> can hide nasty code inside classes
- ORBs written by different vendors -> specs became complicated

Windows Communication Foundation:
- microsoft framework for making service-oriented apps
![[Pasted image 20240731164229.png]]
- Dynamic Link Library (DLL):
	- file format to store collections of code & data to be used by multiple programs simultaneously
	- good for:
		- code reusability -> many apps use same DLL for specific funcs -> reduces redundant code & saves memory space
		- dynamic linking -> app links to DLL at runtime to use func
		- memory efficiency -> DLLs shared by many apps -> only need to load DLL in memory once
- to build own DLL - slide 34-54
- service contract - interface that defines methods exposed by WCF service
	- specifies what operations service provides
	- clients use this to communicate with service and use its methods
- operation contract - method that specifies particular operation that service can do
	- represents individual service methods exposed to clients
	- each contract decorated with attribute
- ServiceBehaviour attribute:
	- customises and configs WCF service behaviour
	- applied to service class and provides way to control service's runtime behaviour
	- options:
		- ConcurrencyMode - how to handle multiple client reqs concurrently
			- single - one req at a time
			- multiple - multiple reqs using multiple threads
		- IncludeExceptionDetailInFaults - include exception details in fault message returned to client in case of unhandled exception
			- true
			- false
		- UseSynchronizationContext - enables synchronisation with current SynchronizationContext -> for UI apps to gather callbacks to UI thread
- bindings: slide 48