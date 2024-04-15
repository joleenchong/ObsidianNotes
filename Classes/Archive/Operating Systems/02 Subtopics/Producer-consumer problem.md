 A synchronisation problem.
- fixed size buffer & producer produces items to then put into buffer
- consumer removes items from buffer to consume
- producer should not produce items into buffer when consumer is consuming item from buffer & vice versa -> buffer should only be accessed by producer / consumer at a time
![[Pasted image 20230403103508.png]] 
- producer [[Processes|process]] produces information consumed by consumer process
- to run concurrent processes, there is a buffer between the processes filled by the producer and emptied by the consumer
	- Unbounded buffer - places no practical limit on size of buffer
	- Bounded buffer - fixed buffer size assumed
	- Buffers can be in the form of shared memory or provided by OS via message passing