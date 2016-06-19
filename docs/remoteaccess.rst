=============
Remote Access
=============

Remote access to our systems is either via SSL VPN, or alternatively some user groups have
dedicated SSH connection via their corporate network.   If you are unsure what method you should
be using to access the systems here, please contact support@cfms.org.uk

---
VPN
---

The VPN is provided by 'Pulse Secure' (previously Juniper Pulse/Network Connect).   There are native
'Pulse Secure' clients for Windows and OSX, or 'openconnect' on Linux.

Windows/macOS
=============

You will be provided the installer for Pulse Connect.   Once installed, create a new connection by clicking
on the '+' and inputting the configuration settings::

  Connection Name: CFMS HPC
  Server URL: TBC

Once configured, click 'connect' and enter your password and when prompted.


Linux
=====

Ubuntu
------

Openconnect is available from the main Ubuntu repositories and can be installed using::

  sudo apt-get update
  sudo apt-get install openconnect

The connection can then be initiated using::

  sudo openconnect --juniper (URL TBC)

and inputting your username and password when requested.

RHEL/CentOS
-----------

Openconnect is available from the EPEL repositories.   If not already enabled, install the EPEL release package::

  sudo yum install epel-release

Then install openconnect::

  sudo yum install openconnect

The connection can then be initiated using::

  sudo openconnect --juniper (URL TBC)

and inputting your username and password when requested.

Fedora
------

Openconnect is available from the Fedora base repositiories and can be installed using::

  sudo dnf install openconnect

The connection can then be initiated using::

  sudo openconnect --juniper cfms-vpn.cfms.org.uk/hpc

and inputting your username and password when requested.
