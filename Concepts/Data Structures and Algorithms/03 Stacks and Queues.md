Lecture 03: Stacks, Queues and Objects

------------
# Stacks
- elements taken out in reverse order
- like taking a plate off/on a stack of plates -> last-in, first-out (LIFO)

Methods:
	- push() - adds new item to top
	- pop() - takes top-most item off
	- top()  - looks at top-most -> does not take off item
	- isEmpty() - checks if stack is empty
Optional:
	- isFull() - checks if stack is full
	- count() - number of items in stack

Pseudocode:
``` pseudocode
Class DSAStack
	fields : stack (<datatype> array), count (int)
	constant : DEFAULT_CAPACITY = 100
	
	Default constructor
		make stack array with DEFAULT_CAPACITY length
		count = 0
	Alternate constructor IMPORT maxCapacity (int)
		make stack array with maxCapacity length

	ACCESSOR getCount IMPORT void EXPORT count
	ACCESSOR isEmpty IMPORT void EXPORT empty (boolean)
		empty = (count = 0)
	ACCESSOR isFull IMPORT void EXPORT full (boolean)
		full = (count = stack.length)

	MUTATOR push IMPORT value EXPORT void
		IF isFull():
			EXCEPTION
		ELSE:
			stack[count] = value
			count = count + 1
	MUTATOR pop IMPORT void EXPORT topVal
		topVal = top()
		count = count - 1
	ACCESSOR top IMPORT void EXPORT topVal
		IF isEmpty():
			EXCEPTION
		ELSE:
			topVal = stack[count - 1]
```

# Queues
- elements taken out in order added
- like... a queue -> first-in, first-out (FIFO)

Methods:
- enqueue() - add item to queue
	- if FIFO, added to the end, if priority, insert in priority order
- dequeue() - take item from front of queue
- peek() - check front item -> does not take it off
- isEmpty() - checks if queue is empty
- isFull() - checks if queue is full
- count() - number of items in queue
```pseudocode 
Class DSAQueue
	fields : queue (<data_type> array), count (int)
	constant : DEFAULT_CAPACITY = 100
	
	Default constructor
		make queue array with DEFAULT_CAPACITY length
		count = 0
	
	Alternate constructor IMPORT maxCapacity (int)
		make queue array with maxCapacity length
		count = 0
		
	ACCESSOR getCount IMPORT void EXPORT count (int)
	ACCESSOR isEmpty IMPORT void EXPORT empty (boolean)
		empty = (count == 0)
	ACCESSOR isFull IMPORT void EXPORT full (boolean)
		full = (count == queue.length)
	
	MUTATOR enqueue IMPORT value EXPORT void
		IF isFull():
			EXCEPTION
		ELSE:
			queue[count] = value
			count = count + 1
	MUTATOR dequeue IMPORT void EXPORT frontVal
		IF isEmpty():
			EXCEPTION
		ELSE:
			frontVal = queue[0]
			FOR i = 0 TO queue.length:
				queue[i] = queue[i + 1]
	ACCESSOR peek IMPORT void EXPORT frontVal
		IF isEmpty():
			EXCEPTION
		ELSE:
			frontVal = queue[0]
```
The following apply to arrays.
## Shuffling Queue
- shuffles items forward when front is dequeued
- every dequeue must move N elements up by 1 -> less efficient
``` pseudocode
Class DSAShufflingQueue
	MUTATOR enqueue IMPORT value EXPORT void
		IF isFull():
			EXCEPTION
		ELSE:
			queue[count] = value
			count = count + 1
	MUTATOR dequeue IMPORT void EXPORT frontVal
		IF isEmpty():
			EXCEPTION
		ELSE:
			frontVal = queue[0]
			FOR i = 0 TO queue.length:
				queue[i] = queue[i + 1]
```

## Circular Queue
- cycles queue around array so previously-dequeued indexes can be reused
- much faster since only need to adjust front index
- to implement wrap-around, simplify by storing count as well as start / end indexes

```
Class DSACircularQueue
	MUTATOR enqueue IMPORT value EXPORT void
		IF isFull():
			EXCEPTION
		ELSE:
			queue[count] = value
			count = count + 1
	MUTATOR dequeue IMPORT void EXPORT frontVal
		IF isEmpty():
			EXCEPTION
		ELSE:
		
```

![[Pasted image 20230321160236.png]]

Tags: #Abstract_Data_Type