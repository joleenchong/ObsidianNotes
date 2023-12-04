Summary:
This paper talks about simulating a hybrid quantum-classical computing environment using a cloud computing environment. This hybrid environment is important as quantum programs cannot be deployed permanently, thus the classical backend is needed to receive user requests. iQuantum accomplishes this by modelling a quantum data centre, computation nodes, qulets, and a computation broker in Java with all their required properties based on the existing classical cloud simulation framework CloudSim. This allows for research into areas like job scheduling algorithms for quantum systems, qubit mapping techniques, and hybrid task orchestration of cloudlets and qulets.

Paper: https://arxiv.org/abs/2303.15729
Github: https://github.com/Cloudslab/iQuantum

----
# Introduction
Research questions:
1. Can we model a hybrid quantum-classical system in a cloud computing environment similar to modelling a classical paradigm?
	- to investigate feasibility of system modelling, identify key elements of hybrid quantum system, how to model them (results in section III and IV)
1. Can we use the proposed simulator to model any use cases in practice?
	- for figuring out usefulness (investigations in section IV)
# Background

Quantum computation is performed on a quantum backend over the cloud -> no need to manage own quantum hardware
![[Pasted image 20231120150547.png]]
The study uses gate-based quantum circuits, where the circuit is built through quantum operations and measurements on qubits using different quantum gates.

Quantum programs cannot be deployed permanently on a quantum computer for multiple executions -> classical cloud backend needed to receive user requests. The task orchestrator classifies tasks and forwards them to quantum / classical nodes to execute. Quantum tasks are called qulets, classical tasks are called cloudlets.

3 metrics for measuring quantum computer performance:
- number of qubits - determines amount of quantum information that can be processed
- quantum volume (QV) - measures quality of qubits
$$V_Q = 2^{min(d,m)}$$ d and m = depth and width of largest square circuit that can be precisely executed (d = m)
- circuit layer operation per second (CLOPS) - measures speed of quantum system thru how many QV circuits can be successfully executed per second
$$(M \times K \times S \times D)/time\;taken$$
- M = 100 -> number of templates
- K = 10 -> number of parameter updates
- S = 100 -> number of shots
- D = $log_2QV$ ->number of QV layers

# Modelling quantum computing environments

Main components of quantum cloud environment:
- quantum data centre ($D_Q$) - centralised hub that manages a set of quantum systems accessible through classical cloud / edge computing system.
	- $D_Q = Q_1, Q_2, ..., Q_n$ where $Q_i$ represents quantum computation node in data centre
- quantum computation nodes ($Q$) - physical quantum computers in a specific quantum data centre, responsible for executing all quantum tasks
	- modelled by set of properties - $Q_i = \set{q^w,q^v,q^s,q^g,q^t,q^e}$
		- $q^w$ - number of qubits
		- $q^v$ - quantum volume of system
		- $q^s$ - quantum computation speed (measured by CLOPS)
		- $q^g$ - list of quantum gate sets supported
		- $q^t$ - qubit topology -> list of all connections btwn pair of qubits within quantum chip
		- $q^e$ - system's error rates
- quantum tasks - units of quantum computation that can be executed on quantum computation node
	- attributes:
		- submission time of qulet
		- quantum gate set in circuit
		- number of qubits (circuit width)
		- number of circuit layers (circuit depth)
		- number of shots (execution repetition)
		- qubit topology in circuit
- quantum computation broker (QBroker) - intermediary entity btwn cloud / edge servers and quantum data centre that schedules qulets to most appropriate quantum computation nodes based on qulet properties and resource availability -> minimises wait times and maximise resource utilisation
	- design and scheduling policy implementation can be customised
![[Pasted image 20231120155642.png]]

# iQuantum design and implementation
![[Pasted image 20231120161542.png]]
Core components are implemented in Java based on discrete-event simulation technique (SimEvent) of CloudSim.
- should research more on SimEvent
![[Pasted image 20231120163054.png]]
- `QDatacenter` - models core infrastructure of data centre
	- consists of collection of `QNode` used for qulet execution
	- configuration of centre including list of quantum nodes (`qNodeList`) defined in `QDatacenterCharacteristics`
- `QBroker` - models broker that handles interactions btwn core simulator and other components
- `QNode` - models quantum node
	- has important metrics like number of qubits, quantum volume, CLOPS, gate set, qubit topology, scheduling policy
- `QubitTopology` - models connectivity among all qubits of quantum node / circuit in qulets
	- used to design qubit mapping strategy
- `Qulet` - a quantum task / circuit to be sent to `QBroker` for scheduling and executed in `QNode` based on scheduling policy defined in `QuletScheduler`
- `QuletScheduler` - abstract class implemented by QNode to model scheduling policy for determining share of resources among multiple qulets

# A sample simulation using iQuantum
Note: reread it to see if i missed anything important.
Steps:
1. Initialise core simulation instance using `iquantum.init()`
2. Create QNode instances
3. Create QDatacenter instance and add QNode instances to it
4. Create QBroker instance and define list of qulets to execute
5. Design and implement customised qulet scheduling policy
6. Submit quletList to qBroker and start simulation. After all tasks complete, stop simulation and print out final result.

# Use cases and extensions
## Quantum job scheduling algorithm design
The QBroker is responsible for job scheduling in a cloud quantum environment. iQuantum can be used to generate cloud workloads and design and evaluate job scheduling algorithms. This area needs active research to optimise resource usage and computation time. Commercial platforms use a fair-share algorithm to ensure fairness when used by the general public.

## Model and design qubit mapping strategies
Qubit / quantum circuit mapping - a mechanism that ensures quantum circuit compatibility with target quantum computer. A quantum circuit can only be executed if qubit connectivity can be mapped to the topology of the quantum chip and if the quantum system supports all single-qubit and multi-qubit gates in the circuit.
iQuantum will be expanded to allow users to design and experiment with circuit mapping techniques.

## Model hybrid quantum-classical computing environment and hybrid task orchestration algorithms
Quantum computing will be used to complement classical computing in executing the tasks best suited for it. Classical computing strengths includes data pre-processing and post-processing while delegating more intensive tasks to quantum systems.
![[Pasted image 20231122133406.png]]
iQuantum is built on top of CloudSim -> can use CloudSim's existing features to model classical cloud stuff.