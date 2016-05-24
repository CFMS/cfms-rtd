========
Software
========

Modules
=======
Almost all software is available via the use of 'Environment Modules' which can easily add and remove software
from your environment, meaning that it is not necessary to add updates to your PATH and LD_LIBRARY_PATH via your
.bashrc file.

Viewing available modules
-------------------------
'module avail' is used to list available modules::
  
  [user@login02 ~]$ module avail

  ----------------------- /net/Modules/modulefiles ------------------------
  mpi/intel/5.0.6.28          compiler/intel/2016.3
  mpi/intel/5.0.1.27          compiler/intel/2015.6
  mpi/openmpi/1.10.2          compiler/gcc/5.0.2
  mpi/openmpi/1.8.4           compiler/gcc/4.9.4
  mpi/openmpi/1.6.5           compiler/gcc/4.8.7

Loading Modules
---------------
'module load <modulename>' will load that module::

  [user@login ~] module load mpi/openmpi/1.10.2
  [user@login ~] module list
  Currently Loaded Modulefiles:
    1) mpi/openmpi/1.10.2

Removing Modules
----------------
'module unload <modulename>' will unload that specific module::
  [user@login ~] module unload mpi/openmpi/1.10.2
  [user@login ~] module list
  No Modulefiles Currently Loaded.

Alternatively 'module purge' will unload any loaded modules.


Compilers
=========

MPI
===

CFD
===

Fluent
------

OpenFOAM
--------
