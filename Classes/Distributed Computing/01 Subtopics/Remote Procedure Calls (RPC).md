A function call that happens elsewhere (e.g. another computer or another process). 	You only send a request to the server to execute the function on your behalf -> server processes req and sends results back to client.

Before it can be used, must define interface of functions you want to call remotely -> done by making Interface Definition Language (IDL) file to specify functions, params, and return types. THE IDL file generates code for both client and server.
- client code will have stub functions to make remote calls
- server code has actual implementation of defined functions

Architecture:
![[Pasted image 20240718223051.png]]

Sending data across network needs to be serialised and deserialised when it reaches its destination. Marshaling deals with converting data btwn different representations within same environment (e.g. OS).

Considerations:
- Security:
	- use secure channels to protect data during transmission
	- consider authentication and authorisation mechanism
- Testing and debugging:
	- test implementation to ensure it works as expected
	- use debugging tools to identify and fix issues that arise
- Scaling
	- need to consider load balancing & other scaling strategies to handle increased traffic and demand

| Pros                                     | Cons                                                                    |
| ---------------------------------------- | ----------------------------------------------------------------------- |
| like calling a local function - familiar | slower due to networks                                                  |
| no need to write lots of network code    | can fail due to networks                                                |
|                                          | programmers can have hard time undestanding that things are distributed |
|                                          | incomprehensible bugs caused by networking errors                       |
