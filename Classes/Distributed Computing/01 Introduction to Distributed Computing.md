In distributed computing, you split parts of an application into multiple processes on multiple machines.

Types:
- Client-server - dumb client access smart server, does all work in server
	- example: SSH, FTP, HTTP
- Peer to peer - no servers, clients all talk btwn each other, no coordinated job is being done
	- example: torrenting, mesh Wi-Fi networks
- Distributed - coordinated, singular app running across all member computers

IPC - inter process communication

To distribute an app, you need an IPC method to support networks:
- TCP / IP - too general purpose -> every app will need you to build a protocol on top of TCP / IP
- [[Remote Procedure Calls (RPC)]]

C# notes:
- namespaces are like java packages
- access modifiers:
	- public - accessible from anywhere
	- private - accessible within same class
	- protected - accessible within same class and derived classes
	- internal - accessible within same assembly
	- protected internal - accessible within same assembly / derived classes
	- private protected - accessible within same assembly & derived classes
- properties:
```c#
public class Person
{
	private string name;
	public string Name {
		get { return name; }
		set { name = value; }
	}
}
```