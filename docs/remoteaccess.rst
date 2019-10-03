=============
Remote Access
=============

Remote access to our systems is either via SSL VPN, or alternatively some user groups have
dedicated SSH connection via their corporate network.   If you are unsure what method you should
be using to access the systems here, please contact support@cfms.org.uk

---
VPN
---

The VPN is provided by 'Pulse Secure' (previously Juniper Pulse/Network Connect).
There are native 'Pulse Secure' clients for Windows and macOS, or 'openconnect' on Linux.

We use Google Authenticator to provide two factor authentication, which provides an additional security layer

Before First Connection
=======================

Open a web browser and open the VPN URL as provided by CFMS support.  Login with your provided credentials and 
follow the instructions to install Google Authenticator and configure it to your account.

Windows/macOS
=============

You will be provided the installer for Pulse Connect.   Once installed, create a new connection by clicking
on the '+' and inputting the configuration settings::

  Connection Name: CFMS HPC
  Server URL: <URL provied by CFMS Support>

Once configured, click 'connect' and enter your password and when prompted.


Linux
=====

Ubuntu
------

Openconnect is available from the main Ubuntu repositories and can be installed using::

  sudo apt-get update
  sudo apt-get install openconnect

The connection can then be initiated using::

  sudo openconnect --juniper <URL provided by CFMS Support>

and inputting your username and password when requested.

RHEL/CentOS
-----------

Openconnect is available from the EPEL repositories.   If not already enabled, install the EPEL release package::

  sudo yum install epel-release

Then install openconnect::

  sudo yum install openconnect

The connection can then be initiated using::

  sudo openconnect --juniper <URL provided by CFMS Support>

and inputting your username and password when requested.

Fedora
------

Openconnect is available from the Fedora base repositiories and can be installed using::

  sudo dnf install openconnect

The connection can then be initiated using::

  sudo openconnect --juniper <URL provided by CFMS Support>

and inputting your username and password when requested.
