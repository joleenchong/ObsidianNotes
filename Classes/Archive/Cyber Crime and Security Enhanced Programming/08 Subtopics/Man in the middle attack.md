The proxy gets controlled by the attacker, so the attacker can intercept communication btwn client and server

Mitigation:
- Use HTTPS - uses TLS to encrypt requests and responses
	- Transport Layer Security (TLS) - cryptographic protocol for authentication and data encryption

Intercepting HTTPS with Burp Suite:
- must decrypt traffic
- if no private key or access to certificates associated with TLS / SSL, cannot decrypt