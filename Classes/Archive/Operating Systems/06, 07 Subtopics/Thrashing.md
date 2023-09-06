Definition:
- occurs when a computer's virtual memory resource are overused -> leads to constant state of [[Paging]] and [[Page fault]]s -> inhibits most application-level processing
- causes performance of a computer to degrade / collapse
- more time paging than executing

If a process does not have enough frames, page fault rate is very high, leading to:
- low CPU utilisation
- OS thinks it needs to increase degree of multiprogramming

How does it occur?
1. system monitors CPU utilisation and tries to maximise CPU utilisation
2. if CPU utilisation is low then increase degree of multiprogramming
	- introduce another process to system
	- use global [[Page replacement algorithm]] (replace any page regardless of process)
3. a process now needs more frames (page faulting and steals frames from other process)
4. other processes start to page fault to retrieve active pages
5. processes get queued up to use paging device, so stop using CPU
6. CPU utilisation is detected to be low; go back to step 1
7. After a few iterations:
	- CPU utilisation has reduced dramatically
	- page faulting high
	- virtually no productivity

How to reduce:
- decrease degree of [[Multiprogramming||multiprogramming]]
- use local / priority replacement algorithm
- Local vs priority:

| Local                                                                            | Priority                                                            |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| only replace frames belonging to this process                                    | only high priority can steal frame from low priority processes      |
| only slows this process down dramatically (slows others as well but not as much) | low priority processes can be thrashing (decrease in speed as well) |
| stops other processes thrashing                                                  |                                                                     |

Why does it happen?
- sum of size of locality > total memory size
	- locality - set of pages actively used together

How to prevent?
- provide process with as many frames as it needs
- use locality model -> states that as a process executes it moves from locality to locality
- [[Working set model]] (strategy) -> starts by looking at how many frames a process is actually using, this defines locality model
- [[Page fault frequency scheme]]