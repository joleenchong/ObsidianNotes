**Theory**

Definition:
- hashing - applying an arithmetic function to key to map it to a location in array for storing data associated with that key
Components:
- Array (table) - stores data
- Hash function - maps keys to int indexes of array

Adding new element:
- key and data is provided
- hash table hashes key and stores both key and data
- key must be unique
- Time complexity: depends on time taken to perform hash calculation (O(?) + O(1) array access time

Hash function properties:
- return indexes that fit within size of array (i.e. \[0 .. arrayLength-1])
	- get modulus of key
	- modulo values - table length, prime numbers as far as possible from powers of 2 (e.g. 769)
- fast to compute
- repeatable for given key -> always returns same index
	- issue: table size is used as modulo -> resizing table changes indexes
	- table must be rebuilt from scratch after resize
- distribute key evenly over full range of array -> minimises collisions
	- collision - when two or more keys map to the same hash index
		- never fill up hash table -> reduces chance of collision
			- allocate twice as much space that'll actually be used
		- use collision-handling method

Collision handling:
- Open addressing: upon collision, jump forward a set amt to new index and try again
	- Linear probing - adds 1 to index and tries again until free slot is found
		- creates primary clusters when encountering collisions -> slows down access time
	- Quadratic probing - stepSize is squared by the probe number at every interation
		- greatly reduces primary clusters -> but makes secondary clusters
		- may miss empty slots
	- Double hashing -  calculates step size based on key
		- greatly reduces secondary clusters
		- guaranteed to visit all slots in prime-sized table
- Separate chaining - key-value pairs are added to linked list anchored at colliding hash index
	- each hashtable entry is a pointer to a linked list
	- collision occurs -> new key-value pair added to linked list
	- O(1) insertion no matter how full table is
	- more complicated

**Practical**
findNextPrime( startVal)
Purpose: to turn keys into hash indexes that can fit the table
```java
public int findNextPrime( int startVal )
{
	int primeVal, rootVal;
	
	if ( startVal % 2 == 0 )
	{
		primeVal = startVal - 1;
	}
	else
	{
		primeVal = startVal;
	}

	boolean isPrime = false;
	
	do
	{
		primeVal = primeVal + 2;
		int i = 3;
		isPrime = true;
		rootVal = sqrt(primeVal);
		
		do
		{
			if ( primeVal % i == 0 )
			{
				isPrime = false;
			}
			else
			{
				i = i + 2;
			}
		} while ( i <= rootVal && isPrime );
	} while ( !isPrime );
	
	return primeVal;
}
```

