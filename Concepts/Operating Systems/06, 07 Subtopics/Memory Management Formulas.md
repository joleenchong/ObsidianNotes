[[Paging]]:
Page number = m - d
where logical address space is 2$^m$ and page size is 2$^d$

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
Example = $\alpha = 0.8$, $\epsilon = 20ns$, $t = 100ns$
- $EAT = 0.8 \times 120 + 0.2 \times 220 = 140ns$ -> 40% slowdown in memory access
- For $\alpha = 0.98$ -> EAT = 122ns

[[Demand paging]] EAT:
- memory access time (*ma*) = 10 to 200ns
- probability of page fault (page fault rate): $0 \leq p \leq 1$
	- if p = 0 -> no page faults
	- if p = 1 -> every reference is a fault
- Effective Access Time:
$$ EAT = (1 - p)* ma + p*$$
