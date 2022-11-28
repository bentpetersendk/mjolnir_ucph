Architecture: hardware
=====

Mjolnir consist of both CPU and GPU nodes, each with very different CPU/GPU and memory setups.
Please note the differences when you are booking your jobs.

.. list-table:: Mjolnir hardware architecture
   :widths: 14 14 20 14 14 20 
   :header-rows: 1

   * - Name
     - Type
     - CPUs/numberTasks
     - GPUs
     - Memory
     - Queue
   * - mjolnirhead01fl
     - login node
     - 96 tasks
     - N/A
     - 125GB
     - No compute allowed, only copy etc. 
   * - mjolnircomp01fl
     - Computation
     - 96 tasks
     - N/A
     - 1TB
     - cpuqueue
   * - mjolnircomp02fl
     - Computation
     - 96 tasks
     - N/A
     - 1TB
     - cpuqueue
   * - mjolnircomp03fl
     - Computation
     - 96 tasks
     - N/A
     - 1TB
     - cpuqueue
   * - mjolnircomp04fl
     - Computation
     - 96 tasks
     - N/A
     - 1TB
     - cpuqueue
   * - mjolnircomp05fl
     - Computation
     - 128 tasks
     - N/A
     - 512gb
     - cpuqueue  
   * - mjolnircomp06fl
     - Computation
     - 128 tasks
     - N/A
     - 512gb
     - cpuqueue
   * - mjolnircomp07fl
     - **Ordered**, will be delivered 8 Jan 2023
     - 64 tasks
     - N/A
     - 1024gb
     - cpuqueue
     
   * - mjolnirgpu01fl
     - Computation
     - 128 tasks
     - 2 x NVIDIA A100-PCI
     - 1TB
     - cpuqueue/gpuqueue
   * - mjolnirgpu02fl
     - Computation
     - 256 tasks
     - 4 x NVIDIA A100-SXM
     - 2TB
     - cpuqueue/gpuqueue
   * - mjolnirgpu03fl
     - Computation
     - 256 tasks
     - 4 x NVIDIA A100-SXM
     - 2TB
     - cpuqueue/gpuqueue  


     
     
     
