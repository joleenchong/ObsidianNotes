An algorithm used together with [[Page replacement algorithm]]. The OS keeps a pool of free frames. 

When a [[Page fault]] occurs:
- select victim frame as before
- write desired page into free frame from pool before victim is written out (so that process can restart sooner)
- write out victim frame to disk & add frame to free frame pool

