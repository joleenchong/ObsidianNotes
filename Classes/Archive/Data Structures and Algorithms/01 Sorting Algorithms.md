Lecture 1: Introduction and Sorting
## Bubble Sort - pretty bad
- sorts array by comparing adjacent pairs and swapping if not in order
- needs multiple passes P (up to N) to fully sort array
- each pass will 'bubble up' largest value to the end
	- so it's called bubble sort cause it slowly pushes up largest values?

**Optimisations**:
- stop sorting when no swaps are needed in pass
- don't check last P values in array

| Pros | Cons |
| ---- | --- |
| Stable sort -> identical values guaranteed to keep ordering | Lots of swaps and comparisons -> less efficient than other O(N^2) algos|

**Best case:** Elements are already in sorted order (only one pass: O(N) )
**Worst case:** Reverse sorted order (complexity: O(N^2) )

Pseudocode:
``` pseudocode
METHOD Bubblesort IMPORT array EXPORT array
	pass = 0
	DO
		sorted = TRUE
		FOR i = 0 TO (array.length - 1 - pass):
			IF (array[i] > array[i + 1]):
				temp = array[i]
				array[i] = array [i + 1]
				array[i + 1] = temp
				sorted = FALSE
		pass = pass + 1
	WHILE (NOT sorted)
```

## Insertion Sort

- takes next element and inserts in sorted order into sub-array that precedes the element
- starts marker at index 1 and moves it up by one after each inserted element, then elements before marker will be sorted
- searches for insert position backwards -> useful for semi-sorted arrays

**Best case:** array in sorted order (complexity: O(N) )
**Worst case**: reverse sorted order (complexity: O(N^2))
**Average case:** go through half the elements in each pass (complexity: O(N^2) )

- Better than bubble sort especially with semi-sorted data
	- elements are placed in sorted position directly while bubble sort swaps around all the time
- stable sort
- still does a lot of swaps per pass

Pseudocode:
``` pseudocode
METHOD InsertionSort IMPORT array EXPORT array
	FOR n = 1 TO array.length:
		i = n
		WHILE i > 0 AND array[i - 1] > array[i]:
			temp = array[i]
			array[i] = array[i - 1]
			array[i - 1] = temp
			i = i + 1
```

## Selection Sort

- select smallest item and swap it with first item -> needs one full pass through array to find smallest
- repeats with second-smallest and swaps with second item
- reoeats until all items have been selected and placed in sorted position

Best = Average = Worst case (complexity: O(N^2) )

- only one swap per pass
- consistent speed
- unstable sort

Pseudocode:
``` pseudocode
METHOD SelectionSort IMPORT array EXPORT array
	FOR n = 0 TO array.length:
		minIdx = n
		FOR j = n + 1 TO array.length:
			IF array[j] < array[minIdx]:
				minIdx = j
		temp = array[minIdx]
		array[minIdx] = array[n]
		array[n] = temp
```