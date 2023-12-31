Test criteria:
- All Combinations (ACoC) - all combinations of blocks from all characteristics must be used
	- number of tests - the product of number of blocks in each partition
- Each Choice (EC) - one value from each block for each partition must be used in at least one test case
	- number of tests - number of blocks in largest partition
- Pair-Wise (PW) - a value from each block for each partition must be combined with a value from every block for each other partition
	- number of tests - at least product of two largest partition
- t-Wise (TW) - a value from each block for each group of t partitions must be combined
	- number of tests - number of choice tests raised to the power *t*
	- if *t* is the number of partitions *Q*, then all combinations (Q-wise = AC)
	- expensive and benefits are not clear
- Base Choice (BC) - certain values are important so they're made the base test and subsequent tests are done for each other block
	- Number of tests - one base test + one test for each other block
- Multiple Base Choice (MBC) - basically more than one base choice blocks is chosen
	- number of tests - M base tests and mi base choices for each partition