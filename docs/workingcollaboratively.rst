=======================
Working Collaboratively
=======================

Shared Workareas
================
Each organisation has a designated workarea at the same level as 'home'.   This
is the location in which any shared data should be stored for group access within
an organisation.

For any collaborative projects between organisations, a dedicated workarea will
be setup under /gpfs/projects with access to each of the nominated parties.


Permissions
===========

Umask
-----
The default permissions provided to any new files give read and write access to
the file owner, and read access to 'group' and 'other'.
::

  [nathharp@clogin02 test]$ ls -l
  -rw-r--r-- 1 nathharp cfms 0 Aug 30 15:41 testfile

If you are writing data out that you would like to allow other users greater access
to, you can use the 'umask' command.
::

  [nathharp@clogin02 test]$ umask 002
  [nathharp@clogin02 test]$ touch testfile
  [nathharp@clogin02 test]$ ls -l
  -rw-rw-r-- 1 nathharp cfms 0 Aug 30 15:42 testfile

This means that users in the group 'cfms' will also be able to write to the file,
and importantly will also be able to delete the file.


Group Ownership
---------------
If you are working with members of another group on a collaborative project, you
can use the 'newgrp' command to set that group as your primary group for a session.
::

  [nathharp@clogin02 test]$ newgrp project1
  [nathharp@clogin02 test]$ touch testfile
  [nathharp@clogin02 test]$ ls -l
  -rw-r--r-- 1 nathharp project1 0 Aug 30 15:56 testfile

This can also be used with the umask command to give write access to other members of
the project group.
