- establishes an upper and lower bound of acceptable [[Page fault]] rate for each process
- if actual rate below lower bound -> process may have too many frames -> remove frames from that process
- if actual rate exceeds higher bound -> process needs more frames -> allocate the process with more frames

| Benefits                                                          | Disadvantages                                                                        |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| directly measure and control page fault rate to prevent thrashing | if page fault rate increases and no free frames then select a process and suspend it |


