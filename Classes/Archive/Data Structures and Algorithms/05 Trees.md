Lecture 05 Trees

**Main topics**
- Binary search trees (BSTs)
	- Structure, data organisation
	- Terminology
	- Methods
- Big-O time complexity analysis
--------------
# Trees
- a data structure to represent hierarchical relationships -> stores set of data organised hierarchically rather than in line

## Terminology
- *Root* - Top-most node that has no parent
- *Parent* - a node that has other nodes spawning from it (e.g. B is parent of A and D)
- *Child* - a node that is the product of another node i.e has a parent (e.g. H is child of F)
- *Leaf* - node with no children (e.g A, C, G, I)
- *Height* - length of path from root to most distant leaf node (E to C, ht = 3)
- *Depth* - path from root to given node (Root E is at depth = 0, G is at depth = 3)
- *Level* - a set of nodes that are all at same depth (A, D, H are at third level. Tree has 4 levels)
![[Pasted image 20230410155251.png]]

## Binary Search Tree
- each node has 0, 1 or 2 children
	- left child and right child
- each node has key for organising trees in a sorted way - key must be unique for searching
- nodes contain value
- sorting is horizontal:
	- every *left* child's key is smaller than key of parent
	- every *right* child's key is larger than key of parent
# Implementation
- put together like doubly linked list -> nodes connected by pointers
- each node has two references - one to left and right child each
	- like the "next" and "previous" pointers of linked lists
	- key for finding, value is data associated with key
- the tree is a reference to root node
## TreeNode class
- key: string / int (must be unique)
- value: object
```java
private class TreeNode
{
	private String m_key;
	private Object m_value;
	private TreeNode m_leftChild;
	private TreeNode m_rightChild;

	public TreeNode (String inKey, Object inVal)
	{
		if (inKey == null)
			throw new IllegalArgumentException("Key cannot be null");
			m_key = inKey;
			m_value = inVal;
			m_rightChild = null;
			m_rightChild = null;
	}
	
	public String getKey() 
	{
		return m_key;
	}
	public Object getValue()
	{
		return m_value;
	}
	public TreeNode getLeft()
	{
		return m_leftChild;
	}
	public void setLeft (TreeNode newLeft)
	{
		m_leftChild = newLeft;
	}
	public TreeNode getRight()
	{
		return m_rightChild;
	}
	public void setRight (TreeNode newRight)
	{
		m_rightChild = newRight;
	}
	
}
```

## BinarySearchTree Class

```java
public class BinarySearchTree
{
	private class TreeNode
	{
		//TreeNode class from prev section
	}
	
	private TreeNode m_root;
	public BinarySearchTree()
	{
		m_root = null; //tree starts empty
	}
	//wrapper methods to call private recursive implementations
	public Object find(String key) { }
	public void insert (String key, Object value) { }
	public void delete (String key) { }
	
	public void display() {  }
	public int height() { }
}
```

### Finding in BST
Steps:
1. Start at root node
2. Compare current node's key with key to find
   - if keys are equal, key is found - return value of node
   - if key to find < node key, go to left child node
   - if key to find > node key, go to right child node
3. if no child exists in chosen branch, then tree doesn't contain key
4. otherwise repeat with child node
Time Complexity:
- very fast
- halves number of nodes to consider every time it moves down a branch -> only checks one node at most for every level in tree
**Recursive find**

```java
public Object find (String key)
{
	return findRec (key, m_root);
}
private Object findRec (String key, TreeNode currNode)
{
	Object value = null;
	
	if currNode == null)
	{
		throw new NoSuchElementException("Key " + key + " not found");
	}
	else if (key.equals (currNode.getKey()))
	{
		value = currNode.getValue();
	}
	else if (key.compareTo(currNode.getKey()) < 0)
	{
		value = findRec(key, currNode.getLeft());
	}
	else
	{
		value = findRec(key, currNode.getRight());
	}
	return value;
}
```

### Insert
- looking for place to add new node
- almost identical to find() but not finding the key
- always adds new node to bottom of branch of tree (creates a new leaf node)
**Recursive insert**
- find null insertion point recursively
Algorithm:
```java
public TreeNode insert(String key, Object data, TreeNode curNode)
{
	return insertRec(key, data, m_root);
}

public TreeNode insertRec(String key, Object data, TreeNode curNode)
{
	TreeNode updateNode = curNode;
	if (curNode == null)
	{
		TreeNode newNode = new TreeNode (key, data);
		updateNode = newNode;
	}
	else if (key.equals(curNode.getKey()))
	{
		throw new Exception("Cannot insert as key already exists in tree");
	}
	else if (key.compareTo(curNode.getKey() < 0))
	{
		curNode.setLeft = insertRec(key, data, curNode.getLeft());
	}
	else
	{
		curnode.setRight = insertRec(key, data, curNode.getRight());
	}
	return updateNode;
}
```

### Delete
- three cases when deleting a node:
	- deleted node has no children
	- deleted node has 1 child
	- deleted node has 2 children
**Successor Node**
- chosen to guarantee that tree will remain binary search tree
	- the next largest from deleted note -> larger than everything in left sub-tree
	- smallest from right sub-tree -> smaller than all nodes on right
	- since successor is being removed from original position, if it has a right child there must be a 'grandparent adopt' for successor

**Recursive delete**
- find node to delete
- when a copy of delete() returns, it returns a pointer to node found at that level of recursion
	- resets the link in parent as recursion unwinds
- after finding delete node, return replacement node / null
- base cases:
	- stop recursion if deleted key not found in tree
	- stop recursion when deleted node is found and after replacement node is identified and descendent links patch
```java
public TreeNode deleteRec(String key, TreeNode curNode)
{
	TreeNode updateNode = curNode;
	if (curNode == null)
	{
		throw new Exception("Key not found");
	}
	else if (key.equals(curNode.getKey()))
	{
		updateNode = deleteNode(key, curNode);
	}
	else if (key.compareTo(curNode.getKey() < 0))
	{
		curNode.setLeft(deleteRec(key, curNode.getLeft());
	}
	else
	{
		curNode.setRight(deleteRec(key, curNode.getRight()));
	}
	return updateNode;
}

public TreeNode deleteNode(String key, TreeNode delNode)
{
	TreeNode updateNode = null;
	
	if (delNode.getLeft() == null && delNode.getRight() == null)
	{
		updateNode = null; //no children
	}
	else if (delNode.getLeft() != null && delNode.getRight() == null)
	{
		updateNode = delNode.getLeft(); // one child - left
	}
	else if (delNode.getLeft() == null && delNode.getRight() != null)
	{
		updateNode = delNode.getRight(); // one child - right
	}
	else // two children
	{
		updateNode = promoteSuccessor(delNode.getRight());
		if (updateNode != delNode.getRight())
		{
			updateNode.setRight(delNode.getRight());
		}
		updateNode.setLeft(delNode.getLeft());
	}
	return updateNode;
}

public TreeNode promoteSuccessor(TreeNode cur)
{
	new TreeNode successor = cur;
	if (cur.getLeft() != null)
	{
		successor = promoteSuccessor(cur.getLeft());
		if (successor == cur.getLeft())
		{
			cur.setLeft(successor.getRight());
		}
	}
	return successor;
}
```

# Types of Trees
- 3 main binary tree classifications:
	- *Complete*
	- *Almost-complete*
	- *Degenerate*

- other types:
	- Strictly binary tree - all nodes have either 0 or 2 children
	- Balanced binary tree - roughly same number of branches on either side of all nodes in tree

## Complete Trees
- all levels in tree are fully filled with nodes
- with L levels, it contains N = 2^(L) - 1 nodes
	- e.g. L = 3, N = 2^(3) - 1 = 8 - 1 = 7 nodes
	- inverted: L = log2N
- important for very consistent structure ->all nodes have 2 children except for last level (0 children)
- fits the most nodes in fewest levels - optimal compactness = optimal efficieny and space usage

## Almost Complete Trees
- the next-best thing when you can't have exactly enough nodes to fill a tree
- time complexity almost identical to complete tree
- Structure - every level is full except the last level, which is filled from left to right
	- left to right is useful for storing binary trees in array (e.g heaps)

**Big-O analysis for find()**
- Best case - root is key we want to find -> O(1)
- Worst case - key is leaf node on last level -> O(log N)
	- almost complete trees have one extra level at 1+log2(N+1) - identical time complexity to complete tree
- average case - key is 2nd bottom level -> O(log N)

**Big-O for insert()**
- best case = worst case = average case -> O(log N)
	- must always insert at null child and only leaf nodes have null children, thus must traverse to last level

**Big-O for delete()**
- best case = worst case = average case -> O(log N)
	- no children - leaf nodes at bottom of tree
	- one child - 2nd last level of tree
	- two children - successor must be at bottom level
Complexity scaling - *O(log N)* vs O(N)
![[Pasted image 20230410220608.png]]

- hard to keep a BST almost-complete

## Degenerate Trees
- every node has only one child
- most inefficient - basically a linked list that uses more memory
- easily happens when inserting items where key are already in sorted order into BST
**Time complexity**
- find || insert || delete:
	- best = O(1)
	- average = worst = O(N)

# Additional tree operations
## Find minimum
- wrappers needed
- max() is the same but working with right children

Recursive:
```java
public int minRec(TreeNode curNode)
{
	int minKey;
	if (curNode.getLeft() != null)
	{
		minKey = minRec(curNode.getLeft());
	}
	else
	{
		minKey = curNode.getKey();
	}
	return minKey;
}
```

Iterative (generally preferred):
```java
public int minIter()
{
	int minKey;
	while (curNode.getLeft() != null)
	{
		curNode = curNode.getLeft();
	}
	minKey = curNode.getKey();
	return minKey;
}
```

## Tree height
- hard to do iteratively
- operations that need to visit multiple nodes work best with recursion

```java
public int height()
{
	return heightRec(m_root);
}

public int heightRec(TreeNode curNode)
{
	int htSoFar, iLeftHt, iRightHt;
	if (curNode == null)
	{
		htSoFar = -1;
	}
	else
	{
		iLeftHt = heightRec(curNode.getLeft());
		iRightHt = heightRec(curNode.getRight());
		if (iLeftHt > iRightHt)
		{
			htSoFar = iLeftHt + 1;
		}
		else
		{
			htSoFar = iRightHt  + 1;
		}
	}
	return htSoFar;
}
```

## Traversal
- three methods:
	- in-order traversal
	- pre-order traversal
	- post-order traversal
- all can be implemented recursively

### In-order
- traverse in ascending sorted order
- good for recovering elements in sorted order from BST
- Algorithm (starts at root):
	- recurse to traverse left-child's branch
	- visit current node
	- recurse to traverse right-child's branch
### Pre-order
- visits nodes in 'parents-first order'
- Algorithm (starts at root):
	- visit current node
	- recurse to traverse left-child branch
	- recurse to traverse right-child's branch
- extracts a list that when re-inserted in that order, recreates the original tree
### Post-order
- visits nodes in 'children-first' order
- Algorithm:
	- recurse to traverse left-child branch
	- recurse to traverse right-child branch
	- visit current node
- can be used to make postfix equations