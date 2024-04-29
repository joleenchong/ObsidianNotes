![[Pasted image 20240322163705.png]]
Creates complex tree of objects to represent complex things using recursive [[aggregation]] -> made to perform operations on itself
- find and return a particular node

Two concrete classes:
<<<<<<< HEAD
- Leaf-node class - for objects that don't contain anything else (e.g. files) / can't be broken down anymore
=======
- Leaf-node class - for objects that don't contain anything else (e.g. files)
>>>>>>> d48770f836e1c92806f65151aec7df40503c7db2
- Composite-node class - for objects that contain leaves and other composites (e.g. directories)
And 1 common [[Interface (Object)]] / abstract superclass (holds shared methods and stuff).

