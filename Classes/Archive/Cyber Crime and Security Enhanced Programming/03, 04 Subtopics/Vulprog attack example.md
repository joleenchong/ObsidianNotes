1. Identify vulnerable functions and insert breakpoint after most vulnerable function
![[Pasted image 20230821155928.png]]
2. Get beginning address of buffer and use `print (long)$rbp - (long) beginning address` to get the number of characters needed to fill the buffer
![[Pasted image 20230821160059.png]]
3. Add +8 to the number -> minimum characters to overflow into $rsp. Characters of shellcode - number = number of characters for padding.
4. Padding + shellcode + padding + new return address. New address should be around start of malicious code. Chosen here is 7f ff ff ff de a0
![[Pasted image 20230821160953.png]]
5. Remember to reverse return address if it is in little endian.
![[Pasted image 20230821161102.png]]
6. After adding new return address to end, use continue to execute the command
![[Pasted image 20230821161202.png]]
