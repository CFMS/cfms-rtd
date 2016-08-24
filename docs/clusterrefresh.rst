===========================
Cluster Refresh Summer 2016
===========================

Overview
========

In the summer of 2016, CFMS will be refreshing it's HPC cluster resource.  The existing
IBM iDataPlex cluster will be retired and replaced by a Cray CS-400 solution, with parallel file storage
provided by ArcaStream, based upon IBM Spectrum Scale (formerly known as IBM GPFS).

The new cluster will be ~5x more powerful than the current iDataPlex cluster, while also being physically
more compact and using the same amount of power.

Timetable
========
Equipment will begin arriving onsite in May 2016.   There will be a phased cutover of service taking place over June-July, during
which there will be a diminished capacity (however, we will keep service level as high as possible)
The iDataPlex system will be completely powered off before the end of September 2016.

What Do I Need to Know?
=======================

New version of Linux
--------------------
The new cluster will be using RHEL/CentOS7 as it's primary OS.   This is running an up-to-date enterprise kernel, plus the most
recent stable drivers.   This also means that we can provide the latest available tools (like compilers) which were no longer
supported on EL5.

This means that although it's possible that your software will continue to run without re-compilation on the new system, it
might be advisable to rebuild with the latest compilers to take advantage of any additional performance.

New job scheduler
-----------------
The new cluster will be running SLURM as the workload scheduler.  We have been running an extended evaluation of SLURM as a
replacement to the legacy GridEngine job scheduler for some time on our newer equipment.  We have found that SLURM is both
more stable than GridEngine, but also much more usable, both for simple and advanced scenarios.

Any existing job submission scripts will need to be modified to work with SLURM, and we will be providing both documentation
and support to help make the transition as easy as possible.

We are aware that some users are developing processes directly against GridEngine - to continue to support this requirement,
we will provide a small test environment continuing to run GridEngine.

New Processors
--------------
The new cluster will include the latest generation Intel E5-26XX v4 (Broadwell) Xeon CPUs, along with Nvidia K80 GPUs.   These
should provide additonal compute peformance per node, while improving FLOPS/watt.

New Storage
-----------
Our existing GPFS storage cluster is to be retired, and replaced with a larger, more stable and more performant solution.   This
will be a new and separate storage system and we are not planning to migrate user data.   However, we will provide guidance and
support to help users move any data that they wish to keep.

Transferring Data
=================

Tools
-----
Data can be easily transferred between clusters.   We would generally recommend the use of 'rsync' to do so.::

  rsync -avh <local directory> <remote server>:<remote directory>

eg::

  rsync -avh mydirectory clogin02:myproject

What Data Should I Transfer
---------------------------
We would recommend using this as an opportunity to go through your data, and chose to transfer only what you intend to keep.
