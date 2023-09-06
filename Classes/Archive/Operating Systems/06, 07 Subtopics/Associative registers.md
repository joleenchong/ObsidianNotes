AKA translation lookaside buffer (TLB).
A memory cache that reduces the time taken to access user memory location. A part of the chip's [[Memory Management Unit]].
- improves virtual address translation speed
- expensive -> typical number of entries limited to 32-104
- can have one for data and another for instruction
![[Pasted image 20230523104318.png]]

Associative memory:
- parallel search; very fast -> address translation (p,d)
1. if A is in TLB, get frame # 
2. otherwise, get frame # from [[Page table]] in memory
3. replace one entry in TLB with new one -> use algorithm, e.g. LRU
4. TLB entries for kernel code can be wired down -> cannot be replaced
	- done as part of instruction pipeline in CPU -> adding no search time penalty
5. On TLB miss, value is loaded into TLB for faster access next time

Address space identification:
- each independent task / process has separate address space with unique 8-bit Address Space Identifier (ASID)
- identifier is stored with each TLB entry to distinguish between entries loaded for different processes
- ASID for running process must match ASID in its TLB entry (address space protection)
- ASID allows processor to [[Context switch]] without invalidating TLB entries (otherwise TLB must be flushed if [[Context switch]])

Effective access time:
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
