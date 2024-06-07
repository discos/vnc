.. _setup:

*****
Setup
*****

This section will guide you through the setup of the dependencies and scripts
needed in order to connect remotely to a DISCOS VNC session.


Install `vncviewer`
===================
In order to be able to view and interact with the telescope's control software
graphical session, the main tool needed is a VNC viewer.
All the DISCOS graphical sessions run on a `TigerVNC <https://tigervnc.org/>`_ server, therefore, the
VNC viewer we suggest to install and use is the `TigerVNC <https://tigervnc.org/>`_ viewer client.
`RealVNC <https://www.realvnc.com/en/connect/download/viewer/>`_ viewer has also been tested and works correctly,
therefore if you already have this viewer installed and executable with the `vncviewer` command, there is no need to switch to another client.

.. note::

   If you are using Microsoft Windows and the WLS system, you need to install
   the regular '.exe' file. Once installed, WSL should automatically detect
   the executable and add its directory to the `$PATH` environment variable.
   The UNIX version of the vncviewer client can also be installed in
   conjunction of an X Window System client, but their performance are not the
   best, therefore we suggest to stick with the regular '.exe' file under
   Windows.


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
