An attack where the server is flooded to shut down the service.

Distributed denial of service - attacker uses a group of remote hijacked systems (botnets) to attack the single target at the same time

Types:
- Volume-based - flood target with large amt of traffic (around 100Gbps+) -> target service bandwidth
	- measured in bits per second (bps)
- Protocol-based - targets vulnerabilities in OSI model layer 3 or 4 (transport or network) -> fills server resources so server cannot store upcoming requests
	- measured in packets per seconds (pps)
- Application-based - targets OSI top layer 7 (application) -> target common internet requests -> hard to determine if attacker is legit user or otherwise

Mitigation:
- traffic filtering & rate filtering - block suspicious traffic and limit number of requests from single source
- intrusion detection / prevention system (IDS/IPS) - monitors and automatically block suspicious traffic patterns
- monitoring and logging - detects and analyse unusual traffic patterns

