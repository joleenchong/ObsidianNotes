Go to page 35 of textbook for exercise 1.2-3 and 1-1

An algorithm is a procedure where an inputted value is turned into a different, outputted value in order to solve a problem. Its criteria are:
- always give the correct result
- give the result in a reasonable time
- can be written in spoken language, as a computer program, or as hardware design

Formal definition of the sorting problem:
- Input: A sequence of n numbers
- Output: A permutation of input sequence such that every number is greater than its preceding number (can't be bothered to write the math notation)
A specified input sequence of this problem is called an instance.

An algorithm is correct if for every input instance, it gives the correct output -> it can solve the problem. Incorrect algorithms can be useful if error rates are controlled (chapter 31 example for large prime numbers).

How to design an algorithm?
- reduce problem to one with good known solution
- write brute force algorithm and use **tricks** to improve it
- Tricks:
	- use better data structures
	- preprocess the input (e.g. sorting) - data formatted to improve algorithm performance
	- use good algorithm design techniques
		- [[03 Divide and conquer|Divide and conquer]]
		- [[06 Greedy algorithms|Greedy approach]]
		- [[09, 10 Dynamic programming|Dynamic programming]]

Analysis:
- Efficiency measure:
	- speed - how long algo takes to produce results
	- space / memory - how much memory is needed to run algo
- time taken scales with size of input (e.g. num of elements, nodes, links)
- use same [[Computation model|computation model]] for analysed algorithms
- Example (insertion sort) from slide 27-30

Big O Notation:
- Asymptotic upper bound (O) - given a function f(n), there is an upper bound called g(n)
- asymptotic tight bound / big theta ($\theta$) -  the middle bound?
- asymptotic lower bound / big omega ($\Omega$)- given a function f(n), there is a lower bound called g(n)
- tight upper bound - when f(n) is smallest possible (not same as big theta)
- Examples- show that 2n + 6 =:
	- O(n):
		- $0 \leq 2n + 6 \leq cn$ - Big O definition
		- $0 \leq 2 + 6/n \leq c$ - take away n
		- TRUE for $n \ge 1$ and $c \ge 8$
		- TRUE for $n \ge 2$ and $c \ge 5$
	- $\Omega$(n):
		-  $0 \leq cn \leq 2n + 6$
		- $0 \leq c \leq 2 + 6/n$
		- TRUE for $n \geq 1$ and $c \leq 2$
	- $\theta$(n):
		- slide 46-47
- when analysing:
	- assigning values, comparisons and mathematical operations are all O(1) -> constants that do not scale exponentially -> do not affect the overall time complexity
	- loops are O(n) - they scale exponentially
		- nested loops are O(n) x O(n) -> O(n<sup>2</sup>)
- always aim for smallest O( g(n) ) expression

SLide 70
Textbook page 36