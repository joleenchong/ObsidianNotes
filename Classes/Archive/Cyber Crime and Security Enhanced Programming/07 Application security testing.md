The practice of evaluating and testing apps to identify and mitigate vulnerabilities and weaknesses that can be exploited.

Stage 1 - Static Code Analysis Testing (SAST)
- identifies problems in source code before compilation and execution
- can find code-level vulnerabilities and coding standard violations (e.g. variable names being uppercase)
- can trace data flow throughout apps and identify issues related to data handing (e.g. data leaks)
- analyse third-party libraries and components to identify known vulnerabilities
- aims to reduce false positives through techniques like pattern matching and code context analysis

Stage 2 - Interactive Application Security Testing (IAST)
- assess the security of web apps and APIs during runtime, either actively running or testing -> combines SAST and DAST

Stage 3 - Dynamic Application Security Testing (DAST)
- evaluates security of web apps and APIs during runtime explicitly as an external attacker

Stage 4 - Runtime Application Self-protection (RASP)
- integrated directly into app to protect against threats during runtime

![[Pasted image 20231107151906.png]]