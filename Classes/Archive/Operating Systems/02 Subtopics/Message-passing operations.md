- Send (message) - message size fixed or variable
- Receive (message)

If two operations want to communicate:
- Establish communication link between them
- Exchange messages via send / receive
- Methods to implement link and send / receive operations:
	- direct / indirect communication
	- synchronous / asynchronous communication
	- automatic / explicit buffering

Direct communication:
- each [[Processes|process]] must explicitly name recipient / sender of the communication
- Primitives used:
	- Send (P, message) - send a message to process P
	- Receive (Q, message) - receive a message from process Q
	- Properties of communication link:
		- links are established automatically
		- a link is associated with exactly one pair of communicating processes 
		- between each pair there exists one link
		- link may be uni-directional but usually bi-directional

Indirect communication:
- mailboxes are an abstract object that processes can put in / remove messages
- each mailbox has unique ID
- processes can communicate only if they share mailbox
	- Primitives used:
		- Send (A, message) - send a message to mailbox A
			- Receive (A, message) - receive a message from mailbox A
	- Properties of communication link:
		- link only established if processes share a common mailbox
		- link may be associated with many processes
		- each pair of process may share several communication links
		- link may be uni-directional or bi-directional
	- Operations:
		- create a new mailbox
		- send and receive messages through mailbox
		- destroy a mailbox
	- Mailbox sharing:
		- Consider processes P1, P2, P3 share a mailbox A, process p1 sends a message to mailbox A while processes P2 & P3 execute a receive from A,
		- *Which process will receive the message sent by P1?:*
			- allow a link to be associated with at most two processes, OR
			- allow only one process at a time to execute a receive operation, OR
			- allow system to select the receiver arbitrarily. Send is notified who receiver is
