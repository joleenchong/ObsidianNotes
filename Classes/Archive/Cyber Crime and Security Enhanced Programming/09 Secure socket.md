Socket programming - connecting 2 nodes on network to communicate with each other
- bound to a local port -> socket address = IP + Port number
- each socket associated with a protocol (UDP & TCP)
- acts as programming interface to app code and transport layer
- socket handle is like file handle

Anatomy:
![[Pasted image 20231107223208.png]]

Problems with sockets:
- no limit on creation, created everytime user does something
- input received not sanitised
- sensitive data sent not encrypted
- no native mechanism for authentication
- data transmission thru socket done in clear text

Secure Socket Layer:
- encrypts data transmitted across the web
- initiates authentication thru handshake btwn 2 devices to ensure both devices trusted
- digitally signs data to verify data not tampered with
- TLS is more improved and secured version of this
