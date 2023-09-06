- Re-orders equation so higher precedence operations come before lower ones
	- get rids of brackets
	- read from left to right
- Postfix:
	- puts operator after operands it applies to 
	- each operator applies to two operands before it
	- operands are added to a pile
		- operator is applied to last 2 operands -> pile is [[03 Stacks and Queues#Stacks]]
	- order of operands is unchanged
	- operators are listed in precedence order
Example:
	Infix: (10.3 * (14 + 3.2) ) / (5 + 2 - 4 * 3)
	Postfix: 10.3 14 3.2 **+ x** 5 2 **+** 4 3 **x - /**
	![[Pasted image 20230318233023.png]]
** is replaced with x because markdown

Process:
1. push operands onto stack until operator is encountered
2. pop off last 2 operands and apply operator to them
3. push result back on stack ready for the next op
4. when no more operands / operators left, answer is the remaining single value on stack

