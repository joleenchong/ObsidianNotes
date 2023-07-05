[[Kernel]] memory is allocated from a free memory pool different than pool for user processes for 2 reasons:
- kernel requests memory in various sizes that might be less than 1 page
- some hardware devices may need [[Contiguous memory allocation||contiguous memory]] location

How to manage free memory for kernel processes?
- [[Buddy system]]
- [[Slab allocation]]

