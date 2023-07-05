The goal of these algorithms is to reduce [[seek time]].

First Come First Serve:
- simplest disk scheduling algorithm
- fair but not fastest
- this shows total head movement of 640 cylinders
![[Pasted image 20230620205027.png]]

Shortest Seek Time First:
- selects request with minimum seek time from current head position.
- may cause starvation of some requests
- this shows 236 cylinders
![[Pasted image 20230620210300.png]]

SCAN / elevator algorithm:
- disk arm starts at one end of disk and moves towards other end, servicing requests until it gets to other end of disk
- shows 236 cylinders
![[Pasted image 20230620210750.png]]

C-SCAN:
- head moves from one end of disk to other, servicing requests as it goes
- after reaching end, head returns to beginning of disk without servicing any requests
- more uniform wait time than SCAN
- the C stands for Circular -> like circular list that wraps around from last cylinder to first one
- shows 382 cylinders
![[Pasted image 20230620211139.png]]

C-LOOK:
- disk arm only goes as far as last request in each direction then reverses direction immediately without first going all the way to end of the disk
- a version of C-SCAN
- shows 322 cylinders
![[Pasted image 20230620212102.png]]
