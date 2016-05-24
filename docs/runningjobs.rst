=============
Managing Jobs
=============

The workload scheduler managing the resources of the cluster is SLURM_.   SLURM is an open source workload manager which is ideal
for clusters and supercomputers of all sizes.

.. _SLURM: http://slurm.schedmd.com/


Checking Available Resources
============================

The command **sinfo** will show the current state of the cluster giving the example below:::

  standard*           up   infinite     51  alloc compa[181-183,185-190,192,195-199,201-220,222-227,229-235,237-238,240]
  standard*           up   infinite      1   idle compa239
  standard*           up   infinite      2   down compa[184,194]
  gpu                 up   infinite      3   idle gpu[1-3]
  highmem             up   infinite      1  down* compb013
  highmem             up   infinite      5  alloc compb[028-030,065-066]
  highmem             up   infinite     10   idle compb[019-026,063-064]

* alloc - node is allocated to a job
* idle - node is idle
* down - node is currently unavailable

Sometimes you will see available resources, but your job still has not started.   This might be because nodes are being held
for another queued job.   Running::

  squeue --start
will show you when your job is due to start.

Submitting Jobs
===============
Any jobs run on the compute nodes in the cluster have to be run through SLURM - access to compute nodes is permitted only to users
who have a job running on that node at that time.

Common Flags
------------

* Timelimit: -t D-HH:MM:SS - sets the runtime limit for the job::

  -t 1-14:13:00

sets a runtime of 1 day, 14 hours, 13 minues and 00 seconds.

* Account: -A <accountname> - submits the job against the named account::

  -A cfms

submits against the CFMS account.

* Number of nodes: -N <number>::

  -N 4

requests 4 nodes from the cluster - commonly used with:

* Tasks per node: --ntasks-per-node=<ntasks> - requests a specific number of cores per node::

  --ntasks-per-node=12

requests 12 cores per node

* Number of cores: -n <number of cores> - used instead of -N/--ntasks-per-node combination::

  -n 120

requests 120 cores



Interactively
-------------
Sometimes it is useful to run jobs interactively on compute nodes (for debugging purposes for example).   SLURM can allow this
through the 'srun' command.::

  [user@login ~]$ srun --pty bash
  [user@compa239 ~]$

This connects you to a compute node, and will give you access to all the resources you have requested.   This can also be done for
parallel jobs::

  [user@login ~]$ srun -N 2 --pty bash
  [user@compa194 ~]$ mpirun hostname
  compa194
  compa195


Batch
-----

Jobs will generally be submitted for batch processing, using a job submission file.   Schduler directives can either be included
along with the 'sbatch' command::

  sbatch -n 120 -t 12:00:00 -A cfms myjob.job

Or included at the top of the job submission file::

  #!/bin/bash -l
  #SBATCH -n 120
  #SBATCH -t 12:00:00
  #SBATCH -A cfms

  mpirun <mpi-executable>

SLURM has tight integration with almost all MPIs, so there is no requirement to create a machinefile to use MPI.  Some MPI do have
SLURM related options (please see MPI section in 'Software' for more information)
