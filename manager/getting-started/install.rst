Install Jexus Manager on Windows
================================

By `Lex Li`_

This page shows you how to install Jexus Manager on Windows.

Background
----------
Jexus Manager is currently in preview and primarily tested on Windows.

Supported Platforms
-------------------
Jexus Manager requires a machine that meets the following requirements,

* .NET Framework 4.6.2 or above is installed.
* Windows 10 and above as client OS.
* Windows Server 2012 and above as server OS.

MSI Based Installation
----------------------
#. Download the MSI installer ``JexusManager_arm64.msi`` or ``JexusManager_x64.msi``
   from `the latest release on GitHub <https://github.com/jexuswebserver/JexusManager/releases>`_ to match your machine hardware.
#. Install from the MSI installer.
#. Launch Jexus Manager from Start menu.

.. note:: If some conditions do not meet, the MSI installer will display an
   error message and indicate how to resolve them.

Portable Installation
---------------------
In certain cases, you might not be able to execute the MSI installer on some
machines (such as without administrator permissions). Then,

#. Install Jexus Manager from the MSI installer on a spare machine with compatible hardware.
#. Copy all files in the installation folder to the target machine.
#. Double click ``JexusManager.exe`` to launch Jexus Manager.

Related Resources
-----------------

- :doc:`/getting-started/features`
- :doc:`/support/known-issues`
- :doc:`/support/troubleshooting`
