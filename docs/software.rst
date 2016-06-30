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

  [user@clogin02 ~]$ module avail

  ----------------------- /net/Modules/modulefiles/mpi ------------------------
  impi/5.0.6.28               openmpi/1.10.2-icc
  impi/5.0.1.27               openmpi/1.8.4-icc
  openmpi/1.10.2-gcc          openmpi/1.6.5-icc
  openmpi/1.8.4-gcc
  openmpi/1.6.5-gcc
  ----------------------- /net/Modules/modulefiles/compilers ------------------------
  intel/2016.3
  cintel/2015.6
  gcc/5.0.2
  gcc/4.9.4
  gcc/4.8.7

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

The system is provided with GCC 4.8.5, but there are also other GCC versions, and also the Intel Parallel Studio XE, which includes C and
Fortran compilers, along with other optimised libraries and tools

MPI
===

Initially OpenMPI and Intel MPI are provided for use on the system.   The environment for these can be loaded using the appropriate modules.
OpenMPI has been provided using both gcc and the Intel compiler (icc).

CFD
===

Fluent
------
Fluent is installed on the cluster.    Your organisation will have to provide licenses for this software to be used however.

OpenFOAM
--------
Different versions of OpenFOAM are installed on the system.
