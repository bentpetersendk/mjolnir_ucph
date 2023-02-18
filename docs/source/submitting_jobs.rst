Submitting jobs
=====
The queueing system SLURM is installed with two queues:

- `gpuqueue` for requesting a GPU
- `cpuqueue` (default) for requesting a CPU.

Both GPU and CPU machines are included in this queue, as the GPU machines also have CPUs available. 

When scheduling a job, take the architecture of the machines into consideration. For more information on Hardware setup, please see the :doc:`hardware` document.

A more elaborate guide to submitting jobs will come soon.


Submitting Jobs to SLURM with sbatch (Quick Guide)
====

SLURM is a job scheduler used on the Mjolnir HPC cluster. `sbatch` is a command-line tool for submitting jobs to SLURM. In this guide, we'll go through the steps for submitting a basic job using `sbatch`.

Step 1: Create a Job Script
---------------------------

The first step in submitting a job to SLURM is to create a job script. The job script is a shell script that specifies the commands and options for your job. Here is an example job script:

.. code-block:: bash

    #!/bin/bash
    #SBATCH --job-name=myjob
    #SBATCH --output=myjob.out
    #SBATCH --error=myjob.err
    #SBATCH --partition=cpuqueue
    #SBATCH --nodes=1
    #SBATCH --ntasks-per-node=1

    echo "Hello, world!"

In this example, the job script specifies a job name, output and error files, the partition to use, the number of nodes, and the number of tasks per node. The last line simply prints "Hello, world!" to the console.

Step 2: Submit the Job
-----------------------

Once you have a job script, you can submit it to SLURM using the `sbatch` command. Here is the command to submit the example job script:

.. code-block:: console

    $ sbatch myjob.sh

This will submit the job to the default queue with the default settings. You can also specify options on the command line to override the options in the job script. For example:

.. code-block:: console

    $ sbatch --partition=gpuqueue --gres=gpu:1 myjob.sh

This will submit the job to the `gpuqueue` queue and request one GPU resource.

Step 3: Monitor the Job
------------------------

After you submit a job, you can monitor its status using the `squeue` command. This command shows a list of all jobs currently running on the cluster. Here is an example of how to use `squeue` to check the status of your job:

.. code-block:: console

    $ squeue -u yourusername

This will show a list of all jobs submitted by `yourusername`. The output includes information such as the job ID, the job name, the partition, the status, and the time the job has been running.

Step 4: View Job Output
------------------------

Once a job has completed, you can view its output and error files. In our example job script, the output and error files are specified as `myjob.out` and `myjob.err`. You can view the contents of these files using the `cat` command. For example:

.. code-block:: console

    $ cat myjob.out

This will show the contents of the `myjob.out` file on the console.

Conclusion
----------

In this guide, we've gone through the basic steps for submitting a job to SLURM using `sbatch`. For more information on `sbatch` and other SLURM commands, please see the official SLURM documentation.
