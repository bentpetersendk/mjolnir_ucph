Software
=====

Software can be loaded in two ways: using a Conda environment or loaded as a module.
For most users, loading the software as a module is the preferred way to work.

Modules
-----
A more extensive guide to using modules will be added soon...

What is a module?
****
The module system is a concept available on most cluster, simplifying the use of different software and software-versions in a precise and controlled manner. In general, more software is installed than the average user will ever use, and often there will be several versions provided for a package where it will be necessary for a user to choose between them. Furthermore, two different software packages might clash with eachother as they could overlap when loaded together. Loading a software as modular packages overcomes this problem, as the module will manage the user environment for the installed software. In each module it is possible to define pre-requisites (other software it is depending on), or define which software can not be loaded at the same time to avoid conflict.






Conda Environments
-----
Version specific conda environments can be located in:

.. code-block:: console

   /projects/mjolnir1/apps/conda/software-version
   
If you want to activate the Conda environment ``bwa version 0.7.17`` you simply type:

.. code-block:: console

   conda activate /projects/mjolnir1/apps/conda/bwa-0.7.17

When you are finished using the software and want to deactivate it, you type:

.. code-block:: console

   conda deactivate

For more information in using ``conda environments`` please refer to:
`Conda userguide <https://docs.conda.io/projects/conda/en/latest/user-guide/index.html>`_


Installed Software
-----
A list of installed software will come...

