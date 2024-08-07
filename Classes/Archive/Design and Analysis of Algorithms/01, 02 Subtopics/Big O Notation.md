 Three types:
-  Asymptotic upper bound / big oh (O) - given a function f(n), there is an upper bound called g(n)
- asymptotic tight bound / big theta ($\theta$) -  worry about this only when O and omega are the same
- asymptotic lower bound / big omega ($\Omega$)- given a function f(n), there is a lower bound called g(n)
- tight upper bound - when f(n) is smallest possible (not same as big theta)

Examples- show that 2n + 6 =:
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
