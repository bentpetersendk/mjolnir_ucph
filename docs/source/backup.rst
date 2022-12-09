Backup
======

In most directories there is a hidden directory called ``.snapshot``. This is your savour. Here you will find a daily backup with a snapshot of your data. The data is kept for 7 days, unless there is a lack of diskspace. You should therefore not rely on that you can always retrieve your files again.

.. image:: backup.png
   :alt: Scrrenshot of .snapshot folder 
   :align: center

In each of the folders you will find a dailysnapshot of files files you had at this particular day. |br|
As an example: ``'Research_performance_repl_reduced _7d_2022-12-07_17:00'`` refers to files from ``7 December 2022 at 17.00``.

If you want to retrieve a file from the backup you need to copy it from the snapshot location to the destinatipn folder. You will not be able to delete any files in the ``.snapshot`` folder as it is a read-only directory.
