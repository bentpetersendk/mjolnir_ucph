Submitting jobs
=====
The queueing system SLURM is installed with two queues:

- `gpuqueue` for requesting a GPU
- `cpuqueue` (default) for requesting a CPU.

Both GPU and CPU machines are included in this queue, as the GPU machines also have CPUs available. 

When scheduling a job, take the architecture of the machines into consideration. For more information on Hardware setup, please see the :doc:`hardware` document.

Submitting Jobs to Mjolnir using sbatch
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

