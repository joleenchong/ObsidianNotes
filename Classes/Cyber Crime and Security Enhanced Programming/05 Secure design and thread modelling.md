Secure design - the practice of designing software system with security as a fundamental consideration from the very beginning of development.
- least privilege - users and components only have minimum access rights necessary to do tasks
- defense in depth - multiple layers of security controls should be implemented to protect against various types of attacks
- fail-safe defaults - design systems to be secure by default, with features disabled unless explicitly enabled

Threat modelling - helps understand system from attacker's perspective

STRIDE:
- Spoofing identity - attacker assumes identity of another entity to gain unauthorised access or deceive users
	- example: phishing attacks trick victims into sharing sensitive info with what they think is a legit source
- Tampering with data - unauthorised modification of data -> leads to unauthorised actions or compromising info's integrity
	- example: [[SQL injection]]
- Repudiation - situations where user performs action and later denies having done so -> accountability and audit trails
	- example: user places order on e-commerce website and claims they never made the purchase
- Information disclosure - exposing sensitive data to unauthorised users
	- example: [[Cross-site scripting attack (XSS)]] exposes users' session cookies
- Denial of service - overwhelming system with malicious traffic or actions
	- example: Distributed Denial of Service (DDoS) attacks
- Elevation of privilege - attacker gains unauthorised access to system or gain higher levels of authorisation than needed

Benefits:
- early detection - helps prevent identified risks in design phase from propagating into final product
- cost-effective - cheaper to fix at early stage than post-development
- improved communication - encourages collaboration between developers, security experts, stakeholders
- prioritisation - focuses on most critical risks

Steps:
- Scope definition - define boundaries and components of system to analyse
- Data flow diagrams - create diagrams showing how data flows through system
- Threat identification - identify potential threats using STRIDE model
- Vulnerability assessment - determine vulnerabilities that might be exploited by identified threats
- Mitigation - devise strategies to mitigate / eliminate identified vulnerabilities
- Review and update threat model as system evolves