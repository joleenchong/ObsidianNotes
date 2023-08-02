[[Paging]]:
Page number = m - d
where logical address space is 2$^m$ and page size is 2$^d$
Frame number = physical address space 2$^m$ - page size 2$^d$
- frame size = page size
---
Effective Access Time (from [[Associative registers]]):
Notation:
- Associative lookup = $\epsilon$ time unit
- memory cycle time = *t* time unit
- Hit ratio = $\alpha$ is the percentage of times that page number is found in associative register

How?
- if page number is in TLB:
$$
time = \epsilon + t
$$
- if page number NOT in TLB:
$$
time = \epsilon + t + t
$$
- EAT:
$$
EAT = (t + \epsilon) \alpha + (2t + \epsilon)(1 - \alpha)
$$
or EAT =  hit ratio(memory cycle time + associative lookup) + (2 x memory cycle time + associative lookup)(1 - hit ratio)
Example = $\alpha = 0.8$, $\epsilon = 20ns$, $t = 100ns$
- $EAT = 0.8 \times 120 + 0.2 \times 220 = 140ns$ -> 40% slowdown in memory access
- For $\alpha = 0.98$ -> EAT = 122ns

[[Demand paging]] EAT:
- memory access time (*ma*) = 10 to 200ns
- probability of page fault (page fault rate): $0 \leq p \leq 1$
	- if p = 0 -> no page faults
	- if p = 1 -> every reference is a fault
- Effective Access Time:
$$ EAT = (1 - p)* ma + p*(page fault time)$$

[[Frame allocation]] schemes:
- Fixed allocation:
	- Equal allocation:
		- *m* frames, *n* processes -> *m* / *n* frames per process
		- put remainder in free frame pool
		- Example: 93 frames, 5 processes -> 18/process, and 3 in free frame pool
	- Proportional allocation - allocate according to size of process
		- s$_i$ = virtual memory required for process p$_i$
		- s = sum of s$_i$
		- m = total number of frames
		- a$_i$ = allocation for p$_i$  $$a_i = \frac{s_i}s \times m$$