Canceling Jobs
*****

Sometimes, you may need to cancel a job that you previously submitted to the SLURM queue. SLURM provides the `scancel` command for this purpose.

To cancel a specific job, you need to know its Job ID (or `JOBID`), which you can obtain from the output of the `squeue` command, or by saving the job ID when you submitted the job.

Canceling a Specific Job
------------------------

To cancel a specific job, run the following command:

.. code-block:: console

    $ scancel JOBID

Replace `JOBID` with the ID of the job you want to cancel.

Canceling Multiple Jobs
------------------------

If you want to cancel multiple jobs at once, you can specify a range of job IDs, separated by commas. For example:

.. code-block:: console

    $ scancel JOBID1,JOBID2,JOBID3

This will cancel the jobs with IDs `JOBID1`, `JOBID2`, and `JOBID3`.

You can also cancel all jobs submitted by a specific user, by running the following command:

.. code-block:: console

    $ scancel -u USERNAME

Replace `USERNAME` with the name of your user.

Canceling a Job Array
---------------------

If you submitted a job array, you can cancel the entire array by canceling the job ID of the array task. For example, if your job array has the ID `123456`, you can cancel the entire array by running the following command:

.. code-block:: console

    $ scancel 123456

This will cancel all tasks in the job array.

Canceling Jobs by Partition or Node
-----------------------------------

You can also cancel all jobs running on a specific partition or node, by using the `--partition` or `--nodelist` option, respectively. For example:

.. code-block:: console

    $ scancel --partition=PARTITION_NAME

This will cancel all jobs running on the partition named `PARTITION_NAME`.

.. code-block:: console

    $ scancel --nodelist=NODE_NAME

This will cancel all jobs running on the node named `NODE_NAME`.

Conclusion
----------

The `scancel` command provides a simple and powerful way to cancel jobs in the SLURM queue. By using the options described in this guide, you can cancel specific jobs, job arrays, or all jobs submitted by a specific user or running on a specific partition or node.
