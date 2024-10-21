.. _setup:

*****
Setup
*****

This section will guide you through the setup of the dependencies and scripts
needed in order to connect remotely to a DISCOS VNC session.

.. note::

   If you need support setting up the system, in case you followed this
   tutorial and something still doesn't work, you can write an e-mail to
   `Giuseppe Carboni <mailto:giuseppe.carboni@inaf.it>`_.


Install `vncviewer`
===================
In order to be able to view and interact with the telescope's control software
graphical session, the main tool needed is a VNC viewer.
All the DISCOS graphical sessions run on a `TigerVNC <https://tigervnc.org/>`_ server, therefore, the
VNC viewer we suggest to install and use is the `TigerVNC <https://tigervnc.org/>`_ viewer client,
you can find the latest release in the `TigerVNC GitHub Releases page <https://github.com/TigerVNC/tigervnc/releases>`_.
`RealVNC <https://www.realvnc.com/en/connect/download/viewer/>`_ viewer has also been tested and works correctly,
therefore if you already have this viewer installed and executable with the `vncviewer` command, there is no need to switch to another client.

Linux systems configuration
---------------------------
In order to install the `vncviewer` command under a Linux distribution, it
should be enough to download it from your system's package manager. For
example, if you are running any recent Ubuntu distribution, the following
set of commands will install the `vncviewer` command for you:

.. code-block::

   $ sudo apt update
   $ sudo apt install tigervnc-viewer

You can check if the setup process was successful by executing the `vncviewer`
command like the following:

.. code-block::

   $ vncviewer -h
   TigerVNC Viewer v1.13.1
   Built on: 2023-03-04 00:19
   ...

Microsoft Windows configuration
-------------------------------
If you are using Microsoft Windows and the WLS system, you need to install
the regular executable file under Windows. The correct file name you have to
download and install looks like `tigervnc64-<version>.exe`. DO NOT install any
vncviewer command under the linux distribution you are using inside the WSL by
using the distro package manager, it won't work. Once you have installed the
tigervnc Windows executable, in order for WSL to detect it, you MUST create a
symbolic link inside the linux distribution under WSL with the following commands:

.. code-block::

   $ cd /usr/bin/
   $ sudo ln -s /mnt/c/Program\ Files/TigerVNC/vncviewer.exe /usr/bin/vncviewer

This will ensure you can execute the `vncviewer` command under linux and the
tigervnc executable will be launched.
A similar configuration must be applied if you use another `vncviewer` client
like `RealVNC`.


Additional dependencies
=======================
The script to connect remotely also requires the following commands to work
properly:

- `netstat` or `ss`, one or the other, they are used to select a local port
  through which the traffic will be travelling
- `nslookup` used to understend whether the script is running inside the SRT
  local area network or not

These applications are mandatory for the script to work and all of them can be
easily installed on a UNIX-like operating system, check online how to install
them onto your machine.


Download the srt-vnc script
===========================

Now that the dependencies have been installed, the next step is to download the
script used to connect to the remote VNC sessions and make it executable.
Download the `srt-vnc <https://github.com/discos/vnc/raw/master/scripts/srt-vnc>`_
script and save it in a directory of your liking.

.. code-block::

   $ cd mydir
   $ wget https://github.com/discos/vnc/raw/master/scripts/srt-vnc .


Now execute the following command in order to make the script executable

.. code-block::

   $ chmod +x srt-vnc

Now you should be ready to connect and open a VNC session.

.. note::

   If you plan on connecting to a graphical session for quick look and data reduction,
   you have to download the `srt-vnc-ql
   <https://github.com/discos/vnc/raw/master/scripts/srt-vnc-ql>`_ script
   instead. The syntax remains the same as shown later in the document, with the
   only exception of the script name which will be `srt-vnc-ql` instead of
   `srt-vnc`.
