Each process is given a priority, the CPU is then allocated to the process with the highest priority (lowest number -> 3 would have more priority than 8).

Internally defined priority - a measurable quantity (e.g. time limits, memory requirements, etc.)
Externally defined priority - based on things outside of the OS (e.g. funding, department, politics)

Starvation may occur for low priority processes -> solve by increasing priority of those processes by time (aging)