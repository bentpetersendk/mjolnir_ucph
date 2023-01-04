Software
=====

Software can be loaded in two ways: using a Conda environment or loaded as a module.
For most users, loading the software as a module is the preferred way to work.

Modules
-----
A more extensive guide to using modules will be added soon...

What is a module?
****
The module system is a concept available on most cluster, simplifying the use of different software and software-versions in a precise and controlled manner. In general, more software is installed than the average user will ever use, and often there will be several versions provided for a package where it will be necessary for a user to choose between them. Furthermore, two different software packages might clash with eachother as they could overlap when loaded together. Loading software as modular packages overcomes this problem, as the module will manage the user environment for the installed software. In each module it is possible to define pre-requisites (other software it is depending on), or define which software can not be loaded at the same time to avoid conflict.

List Available Software
-----
Usingthe command ``module avail`` will list all the software available in the cluster

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

As the output from ''module avail'' is quite long it is recommended to pipe the output into ''less'' and then press ''space'' to change page: ''module avail | less -S''.



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

