Architecture: hardware
=====

Mjolnir consist of both CPU and GPU nodes, each with very different CPU/GPU and memor setups

.. list-table:: Title
   :widths: 16 16 16 16 16 16 
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
     - N/A
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


     
     
     
