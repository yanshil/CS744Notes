# TensorFlow

* Lazy Evaluation. Execute only operators required to compute result.
* Identify location of individual operators
* Simple greedy scheduling strategy (simulation, cost based scheduling)
* Special "Send" and "Receive" nodes.
	* Kernels read / write to device memory
* Fault tolerance
	* checkpointing (enabled by special "save" nodes)
	
## Speeding Up Computation

* GPUs are predominant used

* Distributed ML requires high throughput for 
	* Fast GPU-GPU
	* GPU-GPU single
	* GPU-GPU inner
	* Slowest link is GPU-GPU inter-server communication
	* Largely unaddressed
	* BUt how often is this exercised?