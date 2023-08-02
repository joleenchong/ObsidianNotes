RAID stands for Redundant Array of Independent Disks. RAID is made up of multiple disks working cooperatively

Characteristics:
-  a set of physical disk drives seen by OS as single logical drive
- data is distributed across array of physical drives
- redundant disk is used to store parity info 0> guarantees data recoverability in case of disk failure

Improves:
- Speed
	- disk striping uses group of disks as one storage unit
	- block is broken into several sub-blocks with one sub-block stored on each disk
	- access to sub-blocks can be done in parallel -> faster
- Reliability
	- multiple disk drives -> reliability via redundancy
	- mirroring or shadowing keeps dupes of each disk
	- block interleaved parity -> much less redundancy

RAID consists of Level 0 - Level 6.

Level 0 (Striping):
![[Pasted image 20230621152309.png]]
- Goal - improves performance & capacity (not reliability)
- disk is divided into blocks
- for n-disk array, first n logical strips are physically stored on first strip on each of n disks; 2nd n strips are put in 2nd strip on each disk ...
	- a single request from multiple contiguous strips can be accessed in parallel (from up to n strips) -> increases **effective transfer rate** -> higher data transfer capacity
	- multiple requests - RAID 0 reduces queuing time for each request - higher IO request rate
Level 1 (mirrored):
- ![[Pasted image 20230621154647.png]]
- improves reliability by duplicating all data
	- needs 2x disk space of logical disk that it supports
	- when one drive fails, data still in second drive
- 0 + 1 (the second part is the first layer):
	- ![[Pasted image 20230621154004.png]]
	- a set of disks are striped and stripe is mirrored to equivalent stripe
	- read request is serviced by either 2 disks
	- write request needs updating corresponding strips
	- one disk fail makes entire stripe unavailable -> leaves only mirrored stripe
- 1 + 0:
	- ![[Pasted image 20230621154043.png]]
	- disks are mirrored in pairs -> mirrored pairs are striped
		- one disk fails, mirrored disk and remaining disks are still available 

Level 2:
- ![[Pasted image 20230621161526.png]]
- uses parallel access technique -> all disks participate in execution of every IO request
- error-correcting code is calculated across corresponding bits on each data disk
	- bits of code stored in corresponding bit positions on multiple parity disks
- number of redundant disks is proportional to log value of number of data disks
- only used if many disk errors

Level 3 (bit-interleaved parity):
- ![[Pasted image 20230621181538.png]]
- only needs 1 redundant disk unlike RAID 2
- uses simple parity bit for set of individual bits in same position on all of the data disks
- employs parallel data access with data distributed in small strips
- Reliability:
	-  on drive failure - parity drive is accessed & data is reconstructed from remaining devices
	- Example: RAID 3 with 5 disks: D$_0$ to D$_3$ holds data, D$_4$ is parity
		- Parity calculation: D$_4$(i) = D$_3$(i) ⊕ D$_2($i) ⊕ D$_1$(i) ⊕ D$_0$(i)
		- if D$_1$ fails:
			- D$_1$ = D$_4$(i) ⊕ D$_3$(i) ⊕ D$_2($i) ⊕ D$_0$(i)
- Performance:
	- very high data transfer rates -> data is stripped in very small strips -> good for large transfers
	- does not improve IO rate -> only one IO request can execute at a time

Level 4 (block-level parity):
- ![[Pasted image 20230621181639.png]]
- uses relatively large data strips and independent access technique
	- each member disk operates independently -> can satisfy separate IO request in parallel
	- good for high IO request rates (not high data transfer rates)
- Performance:
	- for small data -> involves 2 reads and 2 writes
		- read old data strip and parity strip
		- write new data and parity strip
	- for large data -> write uses only new data bits -> parity drives updated in parallel with data drives -> no extra reads / writes

Level 5 (block-level distributed parity):
- ![[Pasted image 20230621182827.png]]
- distributes parity strips across all disks -> avoids potential IO bottleneck in RAID 4 parity disk

Level 6: 
- stores redundant info to handle multiple disk failures
- uses error correcting code instead of parity in RAID 5
- needs 2 bits of redundant data for every 4 bits of data -> more expensive than RAID 5 -> can tolerate 2 disk failures
- AKA P + Q redundancy

Note: research parity
Parity generally is the state of being equal. In mathematics, parity is the property of an integer deciding if it's even or odd. A parity bit is a bit added to a string of binary code as a simple form of error detecting code.
https://www.router-switch.com/faq/what-is-parity-in-raid-and-how-parity-works.html
https://www.pcmag.com/encyclopedia/term/raid-parity#:~:text=Parity%20computations%20are%20used%20in,about%20XOR%2C%20see%20OR
https://en.wikipedia.org/wiki/Parity_drive
https://en.wikipedia.org/wiki/Parity_bit

might make each level its own file