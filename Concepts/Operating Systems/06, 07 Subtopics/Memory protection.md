Implementation:
- associating a protection bit with each frame
- valid-invalid bit attached to each entry in [[Page table]]
- valid shows associated page is in process' logical address space -> legal
- shows page is not in process; logical address space

What other bits can be used for protection?
- one bit used to set a page read-write or read-only access
- each attempt to access page is checked against protection bits (any illegal attempt traps OS)

![[Pasted image 20230523112415.png]]

