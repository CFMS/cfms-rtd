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

  ----------------------- /opt/modulefiles/mpi ------------------------
  impi/5.0.6.28               openmpi/1.10.2-icc
  impi/5.0.1.27               openmpi/1.8.4-icc
  openmpi/1.10.2-gcc          openmpi/1.6.5-icc
  openmpi/1.8.4-gcc
  openmpi/1.6.5-gcc
  ----------------------- /opt/modulefiles/compilers ------------------------
  intel/2016.3                gcc/4.9.4
  intel/2015.6                gcc/4.8.7
  gcc/5.0.2


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

Module Conflicts
----------------
Incompatible modules are configured to conflct with each other, and will not allow two conflicting modules to be loaded.  For example, loading two
OpenMPI modules into your environment can cause inconsistent or unexpected results.


Compilers
=========

The system is provided with GCC 4.8.5, but there are also other GCC versions, and also the Intel Parallel Studio XE, which includes C and
Fortran compilers, along with other optimised libraries and tools.

MPI
===

Initially OpenMPI and Intel MPI are provided for use on the system.   The environment for these can be loaded using the appropriate modules.
OpenMPI has been provided using both gcc and the Intel compiler (icc).

OpenMPI
-------
Each version of OpenMPI has been compiled with a specific compiler - if you are planning to build software against a OpenMPI, it is advised
to use that same compiler.   Loading the '-gcc' modules for OpenMPI will not load any additional modules, whereas loading the '-icc' versions will
also load the relevant Intel compiler module.

CFD
===

Fluent
------
Fluent is installed on the cluster.    Your organisation will have to provide licenses for this software to be used.

To run a Fluent job in batch, you will need to provide a journal file.   First create a script 'fluent-batch.sh' with the below content,
updating the 'FLUENTVER' variable to the particular version you would like to run::

  #!/usr/bin/env bash
  #SBATCH -o fluent-%j.out
  FLUENTVER=v161
  HOSTSFILE=.hostlist-job$SLURM_JOB_ID
  JOURNALFILE=$1
  if [ "$SLURM_PROCID" == "0" ]; then
     srun hostname -f | sort > $HOSTSFILE
     /gpfs/apps/ansys_inc/$FLUENTVER/fluent/bin/fluent -pinfiniband -g -t $SLURM_NTASKS -cnf=$HOSTSFILE -ssh 3d -i $JOURNALFILE
     rm -f $HOSTSFILE
  fi
  exit 0

change the permission to allow it to be executed::

  chmod u+x fluent-batch.sh

These jobs can then be submitted as standard sbatch jobs::

  sbatch -N 2 --ntasks-per-node=24 fluent-batch.sh <journal file>

Fluent can also be run interactively in parallel.   Although we generally wouldn't recommend without using in conjunction with a node reservation to
ensure that resources are available.

First create a script 'fluent-interactive.sh' with the below content,updating the 'FLUENTVER' variable to the particular version you would like to run::

  #!/usr/bin/env bash
  FLUENTVER=v161
  HOSTSFILE=.hostlist-job$SLURM_JOB_ID
  if [ "$SLURM_PROCID" == "0" ]; then
     srun hostname -f > $HOSTSFILE
     /gpfs/apps/ansys_inc/$FLUENTVER/fluent/bin/fluent -pinfiniband -t $SLURM_NTASKS -cnf=$HOSTSFILE -ssh 3d
     rm -f $HOSTSFILE
  fi
  exit 0

change the permission to allow it to be executed::

  chmod u+x fluent-interactive.sh

These jobs can then be submitted as standard srun jobs::

  srun -N 2 --ntasks-per-node=24 --x11=first fluent-interactive.sh


OpenFOAM
--------
Different versions of OpenFOAM are installed on the system.   Please see /gpfs/apps/OpenFOAM/README for the environment that is required to load
a particular version.
