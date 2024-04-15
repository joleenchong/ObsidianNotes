Schedules processes according to the length of its next CPU burst. Gives minimum average waiting time, turnaround time, response time for given set of processes -> optimal. A variation of [[Priority Scheduling]].

Two schemes:
- non-preemptive - once CPU is given to process, cannot be preempted until it finishes CPU burst
- preemptive  - if new process arrives with less CPU burst time than remaining time of current process, preempt -> Shortest-Remaining-TIme-First

Advantages:
- superior turnaround time to shortest process because short job is given immediate preference to running longer job
- high throughput

Disadvantages:
- elapsed time must be recorded -> additional processor overhead
- longer processes may starve
