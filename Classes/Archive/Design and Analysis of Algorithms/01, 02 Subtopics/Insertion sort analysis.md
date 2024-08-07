```python
def insertionSort(array):
	for i in range(1,len(array)): # times = n
		key = array[i] # times = n - 1
		j=i-1 # times = n - 1
		while j>=0 and key < array[j]: # times = sum of ti + 1, i = 1, for each n
			array[j+1] = array[j] # times = sum of ti, i = 1, for each n 
			j -= 1 # times = sum of ti, i = 2, for each n
		array[i+1] = key # times = n - 1
```
- cost - constant number of steps used to execute operation in line j
	- each step is 1 cost -> total cost = 7
- time - number of elements the i key has to travel to get in proper place for i
- to calc running time, do the sum of cost of each line multiplying time of each line:
$$T(n)=c_1n + c_2(n-1) + c_3(n-1) + c_4\sum_{i=1}^n(t_i+1) + c_5\sum_{i=1}^n(t_i) + c_6\sum_{i=1}^{n}(t_i) + c_7(n-1)$$

Best case - array already sorted:
- line 4 - t<sub>i</sub> = 0 for i = 1, 2, 3, ..., n
	- therefore c4(t<sub>i</sub> + 1) = c5(0 + 1) = c4(n-1)
	- c5(t<sub>i</sub>) = c6 = 0
- T(n) = (c1 + c2 + c3 + c4 + c7)n - (c2, c3, c4, c7) -> an + b

Worst case - array reverse sorted:
- c4(t<sub>i</sub> + 1) = c4(i-1+1) = c4(i = ( n ( n+1 ) / 2 ) - 1)
- c5(t<sub>i</sub>) = c5(i - 1) = c5( n(n-1) / 2 ) (same for c6)
I'm not gonna write the full equation, it's an<sup>2</sup> + bn + c

You get the value that has the most effect on the rate of growth to get the time complexity -> $\Theta$(n<sup>2</sup>)
