Managing Servers
================

By `Lex Li`_

This page shows you the main features of Jexus Manager.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
Jexus Manager is designed to be compatible with Microsoft IIS Manager. Though
it is still in beta, many features are already well developed and tested.

The management features require a specific server to be connected to, and then
you can review or change settings.

Default Servers
---------------
Default server instances are displayed automatically if they are detected, so
that they don't need to be manually added.

Jexus Manager detects the following servers and shows them under Connections
panel.

Global IIS Express
^^^^^^^^^^^^^^^^^^
If a global IIS Express configuration file can be found at
``%userprofile%\documents\iisexpress\config\applicationhost.config`` or
``%userprofile%\my documents\iisexpress\config\applicationhost.config``, a
default server called "IIS Express" is automatically created by Jexus Manager.

Local IIS
^^^^^^^^^
If local IIS is installed and its config file is at
``%windir%\system32\inetsrv\config\applicationhost.config``, a default server
with the machine name is automatically created by Jexus Manager.

Add New Servers
---------------
Different types of servers can be added to Jexus Manager, which includes IIS
Express and remote Jexus web servers.

Add IIS Express From Custom Configuration File
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
#. By clicking "File | Connect to a Server…” menu item, the wizard starts,

   .. image:: _static/add_server_types.png

#. Choose IIS Express and click "Next" button.

#. Specify full path of the configuration file (.config) in the text box, or
   click "..." button to browse the file system,

   .. image:: _static/add_server_iis_express_file.png

#. Click Next button.

#. Give this connectioni a unique and meaningful name.

   .. image:: _static/add_server_name.png

#. Click "Finish" button.

Add IIS Express From Visual Studio 2015 Solution File
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Visual Studio 2015 adds custom IIS Express configuration to new projects at
``($SolutionDir)\.vs\config\applicationHost.config``, but this file is hidden
by default.

.. note:: IIS Express custom configuration is documented in `this blog post <http://blogs.msdn.com/b/webdev/archive/2015/04/29/new-asp-net-features-and-fixes-in-visual-studio-2015-rc.aspx>`_ .

#. By clicking "File | Connect to a Server…” menu item, the wizard starts,

   .. image:: _static/add_server_types.png

#. Choose IIS Express and click "Next" button.

#. Specify full path of the solution file (.sln) in the text box, or click
   "..." button to browse the file system,

   .. image:: _static/add_server_iis_express_file.png

   Jexus Manager takes care of the rest to manage web sites and applications.

   .. note:: For new projects/solutions, please debug/run them at least once
      in Visual Studio, so that IIS Express configuration file can be added.

#. Click Next button.

#. Give this connectioni a unique and meaningful name.

   .. image:: _static/add_server_name.png

#. Click "Finish" button.

Manage Servers
--------------
Once a server is added, sites and applications can be managed by choosing one
of the categories in the middle panel.

.. image:: /_static/jexus.png

.. note:: If the server node is not yet expanded for management, double click the node so that Jexus Manager tries to load its configuration.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/support/known-issues`
- :doc:`/support/troubleshooting`
