An interrupt generated when a page needed by a process is not in memory -> [[Page fault]]

Handling procedure:
1. Check if reference address is valid (from internal [[Process Control Block]])
2. If invalid, terminate with an error.
3. Else, find free frame in memory (use free frame list)
4. Schedule disk read operation to read page into allocated frame
5. After reading, modify [[Page table]]
6. Restart instruction that was interrupted by trap
