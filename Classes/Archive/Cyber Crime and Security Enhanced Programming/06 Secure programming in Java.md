Types of security bugs:
- Time-related vulnerability (TIM)
- Software environment related vulnerability (ENV)
- Security design defect vulnerability (SDD)
- Hardware design fault vulnerability (HDF)
- Memory related vulnerability (MEM)
- Logical resources related vulnerability (LOG)
- Numerical errors related vulnerability (NUM)
- Unknown vulnerability (UNK)

Path traversal:
- a web / enterprise app vulnerability that allows an attacker to read files on host machine without having privileges
- How it can happen:
	1. Traversal attempt - attacker manipulates user input using special characters like `../`, `%2e%2e%2f` (URL-encoded representation) to navigate up directory structure
	2. Unauthorised access - if app fails to validate input correctly, attacker can access files / directories outside of intended scope (e.g. config files, system files, etc.)
- Mitigation:
	- input validation - ensure user-supplied paths are within intended directory structure
	- canonicalisation - use built-in Java methods like `File.getCanonicalPath()` -> eliminates directory traversal attempts by resolving path to absolute forms
	- security libraries - prevented through libraries like Apache Commons IO's FilenameUtils, Path class in Java's java.nio.file package

Integer Overflow:
- occurs when arithmetic operation attempts to create numeric value outside of range that can be represented
```java
int maxValue = Integer.MAX_VALUE; //2147483647
int overflowedValue = maxValue + 1;
```
- can lead to undefined behaviour:
	- wraparound - value may wrap around from max to min value and vice versa
	- incorrect calculations - result may be incorrect, could lead to unintended program behaviour
	- security risks - if occurs in security-critical code, could be exploited by attackers to manipulate program behaviour / security checks
- Mitigation:
	- choose appropriate data types for expected range of values in calculations
	- range checking - implement range checks and error handling to detect and handle potential overflows
	- use libraries - libraries like Apache Commons Lang provides utilities for safe arithmetic operations to prevent overflows
