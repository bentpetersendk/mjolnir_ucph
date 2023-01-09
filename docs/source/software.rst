Software
=====

Software can be loaded in two ways: using a Conda environment or loaded as a module.
For most users, loading the software as a module is the preferred way to work.

Modules
-----

What is a module?
****
The module system is a concept available on most cluster, simplifying the use of different software and software-versions in a precise and controlled manner. In general, more software is installed than the average user will ever use, and often there will be several versions provided for a package where it will be necessary for a user to choose between them. Furthermore, two different software packages might clash with eachother as they could overlap when loaded together. Loading software as modular packages overcomes this problem, as the module will manage the user environment for the installed software. In each module it is possible to define pre-requisites (other software it is depending on), or define which software can not be loaded at the same time to avoid conflict.

Working with modules
****
Using the command ``module avail`` will list all the software available in the cluster (a complete list can be found further down this page).

.. code-block:: bash

  $ module avail
  --------------------------- /opt/software/modules ------------------

  anaconda2/4.0.0    ccp4/8.0               cuda/11.4    gcc/5.5.0        lapack/3.10.0        ngsadmix/1.0.0  python/3.9.7          
  anaconda3/4.0.0    ccpem/1.5.0            cuda/11.5    gcc/8.2.0        libxkbcommon/1.3.0   nodejs/14.17.0  python/3.9.9
  anaconda3/5.3.1    ccpem/1.6.0            cuda/11.6    gcc/10.2.0       libxscrnsaver/1.0.0  openjdk/11.0.0  python2/2.0           
  anaconda3/2020.11  cellranger-arc/2.0.0   cuda/11.8    gcc/11.2.0       lightgbm/3.3.2-cpu   openjdk/13.0.1  qpdf/10.3.1           
  anaconda3/2021.05  cellranger-atac/2.0.0  cudnn/8.1.1  gctf/1.06        ltr-retriever/2.9.0  openmpi/4.1.0   R/3.5.0               
  anaconda3/2021.11  cellranger/2.0.0       cudnn/8.2.1  genozip/11.0.11  mageck/0.5.9.4       openssl/1.1.1j  R/3.6.1
  ...

  -------------------------- /projects/mjolnir1/apps/modules ------------------------
  abricate/1.0.1                 cmake/3.22.2           geos/3.10.2            megahit/1.2.9           plink/1.90b6.21          
  abyss/2.1.0                    cmake/3.25.1           geos/3.11.1            megan/6.21.7            plink2/2.00a2.3          
  abyss/2.3.4                    colorama/0.4.4         gffcompare/0.11.2      meme/5.4.1              plotly/5.1.0             
  abyss/2.3.5                    colorama/0.4.6         ghc/8.10.7             metabat2/2.15           plotly/5.11.0            
  adapterremoval/2.3.2           contammix/1.0.11       glimpse-bio/1.1.1      metabolic/4.0           pmdtools/0.60            
  adapterremoval/2.3.3           conterminator/1.c74b5  glimpse/4.18.7         metacache/2.2.1         poetry/1.1.13            
  adapterremovalfixprefix/0.0.5  crux-toolkit/3.2       gnu-parallel/20161122  metacache/2.2.3         poetry/1.3.1             
  admixfrog/20221018             crux-toolkit/4.1       gnuplot/5.4.3          metagenome-atlas/2.8.2  polypolish/0.5.0         
  ...

.. tip::

  As the output from ``module avail`` is quite long, it is recommended to 
  pipe the output into ``less``
  To get around this you can do the following,

  .. code-block:: bash

    $ module avail | less -S

To see what a module actually is doing you can use ``module show <module
name>``. Modules are typically not doing much more than prepending/appending
things to key environment variables like ``$PATH``, ``$LD_LIBRARY_PATH`` and so
on.

.. code-block:: bash

  $ module show adapterremoval
  module show adapterremoval
  -------------------------------------------------------------------
  /projects/mjolnir1/apps/modules/adapterremoval/2.3.3:

  module-whatis   {AdapterRemoval 2.3.3 searches for and removes remnant adapter sequences from High-Throughput Sequencing (HTS) data and (optionally) trims low quality bases from the 3' end of reads following adapter removal. AdapterRemoval can analyze both single end and paired end data, and can be used to merge overlapping paired-ended reads into (longer) consensus sequences. Additionally, Additionally, AdapterRemoval can construct a consensus adapter sequence for paired-ended reads, if which this information is not available.}

  conflict        adapterremoval
  prepend-path    PATH /projects/mjolnir1/apps/conda/adapterremoval-2.3.3/bin
  NOTE: This is a conda-environment and conflicts with dependencies of other modules may occur
  -------------------------------------------------------------------

Modules can be loaded with the command ``module load <module-name>``. 
If you want to load *adapterremoval version 2.3.3* you simply type: ``module load adapterremoval/2.3.2``


Load/Unload Modules
****

You can see which modules you have loaded with: ``module list``

.. code-block:: bash

  $ module list
  Currently Loaded Modulefiles:
  1) adapterremoval/2.3.3   2) bwa/0.7.17   3) tensorflow/2.10.0
  
Modules can have multiple versions of the software. You can see the various 
versions with ``module avail <modulename>``

.. code-block:: bash

  $ module avail bwa
  bwa/0.7.15  bwa/0.7.17
  
You can also search for all modules with a specific keyword in their 
description using: ``module apropos <keyword>``

.. code-block:: bash

  $ module apropos bwa
  bwa/0.7.15: BWA 0.7.15 is a software package for mapping low-divergent sequences against a large reference genome, such as the human genome. It consists of three algorithms: BWA-backtrack, BWA-SW and BWA-MEM. The first algorithm is designed for Illumina sequence reads up to 100bp, while the rest two for longer sequences ranged from 70bp to 1Mbp. BWA-MEM and BWA-SW share similar features such as long-read support and split alignment, but BWA-MEM, which is the latest, is generally recommended for high-quality queries as it is faster and more accurate. BWA-MEM also has better performance than BWA-backtrack for 70-100bp Illumina reads.
  bwa/0.7.17: BWA 0.7.17 is a software package for mapping low-divergent sequences against a large reference genome, such as the human genome. It consists of three algorithms: BWA-backtrack, BWA-SW and BWA-MEM. The first algorithm is designed for Illumina sequence reads up to 100bp, while the rest two for longer sequences ranged from 70bp to 1Mbp. BWA-MEM and BWA-SW share similar features such as long-read support and split alignment, but BWA-MEM, which is the latest, is generally recommended for high-quality queries as it is faster and more accurate. BWA-MEM also has better performance than BWA-backtrack for 70-100bp Illumina reads.
  circularMapper/1.93.5: circularmapper 1.93.5 A method to improve mappings on circular genomes, using the BWA mapper.

You can load a module by doing:

.. code-block:: bash

  # Load the latest version of the module
  module load modulename

  # Load a specific version of a module
  module load modulename/version
  
You can unload a module:

.. code-block:: bash

  module unload modulename

You can also unload ALL loaded modules:

.. code-block:: bash

  module purge

Listing all installed modules
****
The following software can be loaded as modules. 
You can sort after "date" to see the newest installed.

.. raw:: html

       <iframe class="airtable-embed" src="https://airtable.com/embed/shrSAy6vSkKIHQbTz?backgroundColor=yellow&viewControls=on" frameborder="0" onmousewheel="" width="100%" height="533" style="background: transparent; border: 1px solid #ccc;"></iframe>



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

