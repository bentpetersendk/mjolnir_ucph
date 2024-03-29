Submitting jobs
=====
The queueing system SLURM is installed with two queues:

- `gpuqueue` for requesting a GPU
- `cpuqueue` (default) for requesting a CPU.

Both GPU and CPU machines are included in this queue, as the GPU machines also have CPUs available. 

When scheduling a job, take the architecture of the machines into consideration. For more information on Hardware setup, please see the :doc:`hardware` document.

**Remember**

The higher the job’s resource requirements, the longer it will take to find the resources to schedule it - so only book what you need. Your usage is computed using memory and CPU you asked for, not the actual usage. The higher your required usage, the lower priority your job will have.
When you book a number of CPUs - then it must be the same as you are using in the command line. Fx, if you are running `bwa -t 4`, then you also need to book 4 CPU's.

Don't ask for more resources than you actually need. You will loose priority on your next jobs running and your collegues jobs will be queued longer than is needed.

Submitting an Interactive Job using `srun`
*****

`slurm` provides the `srun` command to submit interactive jobs on a compute node. Interactive jobs allow users to work directly on a compute node while monitoring their work in real time. In `srun`, users can specify a number of resources such as CPU, memory, and time requirements. Here is how to use `srun` to submit an interactive job with specific resource requirements.

1. Open a terminal and log in to the cluster.

2. Start an interactive session by running the following command:
    
.. code-block:: console

    $ srun --pty bash

This command requests an interactive session on a compute node with a bash shell.

3. Specify the resource requirements by including one or more of the following options:

.. code-block:: console

    - `--cpus-per-task`: Number of CPUs per task
    - `--mem`: Memory per node (e.g., `--mem=4G`)
    - `--time`: Time limit for the job (e.g., `--time=2:00:00` for 2 hours)

For example, to request 2 CPUs, 4 GB of memory and 1 hour walltime, use the following command:

.. code-block:: console
   
   $ srun --cpus-per-task=2 --mem=4G --time=1:00:00 --pty bash

4. When the compute node is allocated, you will be logged in to the node with a bash shell. You can run your commands here as you would in a terminal.

5. When you are finished with your work, exit the compute node by typing `exit` in the terminal.

That's it! By following these steps, you can submit an interactive job with specific resource requirements using `srun`.


Submitting Jobs using `sbatch`
*****

Mjolnir is a high-performance computing cluster that uses the SLURM scheduler to manage resources and jobs. To submit jobs to Mjolnir, you can use the `sbatch` command. This guide provides an advanced overview of how to submit jobs to Mjolnir using `sbatch`.

Step 1: Prepare your Script
---------------------------

Before submitting a job to Mjolnir, you need to write a script that specifies the commands you want to run on the cluster. This script should be a plain text file containing a list of commands to be executed.

Here is an example script:

.. code-block:: bash

   #!/bin/bash
   #SBATCH --job-name=myjob
   #SBATCH --output=myjob.out
   #SBATCH --error=myjob.err
   #SBATCH --ntasks=1
   #SBATCH --cpus-per-task=4
   #SBATCH --mem-per-cpu=8G    # memory per cpu-core
   #SBATCH --time=01:00:00
   #SBATCH --mail-type=begin        # send email when job begins
   #SBATCH --mail-type=end          # send email when job ends
   #SBATCH --mail-type=fail         # send email if job fails
   #SBATCH --mail-user=your mail address

   echo "Hello world!"

The first line of the script (`#!/bin/bash`) tells the system that this is a bash script. The remaining lines starting with `#SBATCH` are directives for `sbatch` that specify various options for the job. For example, the `--job-name` option specifies the name of the job, the `--output` option specifies the file where stdout files should be written, and the `--time` option specifies the maximum time that the job is allowed to run. See the `sbatch` man page for a complete list of options.

*Remember to always specify the amount of cpu's and memory. If you don't the default values will be used and that will result in your job queuing for a long time.*

Step 2: Submit your Job
------------------------

Once you have a job script, you can submit it to SLURM using the `sbatch` command. To submit your job to Mjolnir, use the `sbatch` command followed by the name of your script:

.. code-block:: console

    $ sbatch myscript.sh

This will submit the job to the default queue with the default settings. You can also specify options on the command line to override the options in the job script. For example:

.. code-block:: console

    $ sbatch --partition=gpuqueue --gres=gpu:1  myscript.sh

This will submit the job to the `gpuqueue` queue and request one GPU resource.

In both cases you will receive a job ID as output. 

After you submit a job, you can monitor its status using the `squeue` command. This command shows a list of all jobs currently running on the cluster. Here is an example of how to use `squeue` to check the status of your job:

.. code-block:: bash

   $ squeue -u your_username

This will show a list of all jobs submitted by `your_username`. The output includes information such as the job ID, the job name, the partition, the status, and the time the job has been running.

Step 3: Monitor your Job
------------------------

While your job is running, you can monitor its progress using the `squeue` command:

.. code-block:: bash

   $ squeue -j job_id

This will show you the status of your job, including its current state, the amount of time it has been running, and the amount of resources it is currently using.

Step 4: View Job Output
------------------------

Once a job has completed, you can view its output and error files. In our example job script, the output and error files are specified as `myjob.out` and `myjob.err`. You can view the contents of these files using the `cat` command. For example:

.. code-block:: console

    $ cat myjob.out

This will show the contents of the `myjob.out` file on the console.

Conclusion
----------

By following the steps outlined in this guide, you should be able to submit jobs to Mjolnir using `sbatch`. Remember to consult the `sbatch` man page for a complete list of options and to monitor your jobs using `squeue`. For more information on `sbatch` and other SLURM commands, please see the official SLURM documentation.


Submitting batch arrays
*****

Submitting batch arrays is a powerful way to automate running large numbers of similar jobs. Batch arrays are a set of jobs with identical code and parameters, but different input files. Each job in the array is identified by a unique index that is passed as an argument to the job script.

In this guide, we will discuss how to submit batch arrays to Slurm.

*Prerequisites*
Before we start, you should have a basic understanding of how to submit jobs to Slurm using sbatch, as well as the syntax for writing job scripts. You should also have a set of input files that you want to process in a batch array.

Step 1: Create a Job Script
---------------------------

The first step is to create a job script that will run a single job in the batch array. All of the parameters (--cpus-per-task, --mem-per-cpu, --time, etc) will be set for every individual job running in the batch array. The script should use the SLURM_ARRAY_TASK_ID environment variable to identify which input file to process.

Here is an example job script for processing input files using the Python script "process.py":

.. code-block:: bash

    #!/bin/bash
    #SBATCH --job-name=myjob
    #SBATCH --output=myjob.%A.%a.out
    #SBATCH --error=myjob.%A.%a.err
    #SBATCH --array=1-10%4
    #SBATCH --time=00:10:00
    #SBATCH --ntasks=1
    #SBATCH --cpus-per-task=1
    #SBATCH --mem-per-cpu=10

    echo "Processing input file input_${SLURM_ARRAY_TASK_ID}.txt"
    python process.py input_${SLURM_ARRAY_TASK_ID}.txt

Let's break down the SLURM directives used in this script:

- `--job-name`: A descriptive name for the job.
- `--output`: The name of the file where Slurm will write the standard output of the job.
- `--error`: The name of the file where Slurm will write the standard error of the job.
- `--array`: A range of indices for the batch array. In this example, we are submitting a batch array with indices 1-10, with a maximum of 4 jobs running in parallel
- `--time`: The maximum amount of time that the job can run. In this example, the job can run for up to 10 minutes.
- `--mem-per-cpu`: The amount of memory allocated per CPU for the job.

Note that the input file is specified using the SLURM_ARRAY_TASK_ID environment variable, which takes on the values specified in the --array option. In this example, the input files are named input_1.txt, input_2.txt, ..., input_10.txt.

Step 2: Submit the Batch Array
---------------------------

To submit the batch array, use the sbatch command with the job script:

.. code-block:: bash

    $ sbatch myjob.sh

This will submit the batch array to Slurm. You can use the squeue command to check the status of the jobs:

.. code-block:: bash

    $ squeue -u username

Step 3: Monitor the Progress of the Batch Array
---------------------------

You can monitor the progress of the batch array using the sacct command:

.. code-block:: bash

    $ sacct -j <jobid> --format=JobID,JobName,Partition,AllocCPUs,State,ExitCode,Elapsed

This command will show you the status of each job in the batch array, including its state and exit code.

Step 4: Post-processing
---------------------------

After the batch array has finished running, you may want to process the output files. In our example, the output of each job is written to a separate file with a unique name

Batch arrays are a powerful tool for managing and executing large numbers of similar jobs. With Slurm and Mjolnir, you can easily submit and manage batch arrays to speed up your workflow and increase efficiency.
