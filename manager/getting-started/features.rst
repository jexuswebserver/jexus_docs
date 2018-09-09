Managing IIS Express Servers
============================

By `Lex Li`_

This page shows you how to add IIS Express servers in Jexus Manager.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
You need to add an IIS Express server in Jexus Manager before managing its
configuration.

Global IIS Express
------------------
In older Visual Studio releases (such as 2012/2013), a global IIS Express
configuration file can be found at
``%userprofile%\documents\iisexpress\config\applicationhost.config`` or
``%userprofile%\my documents\iisexpress\config\applicationhost.config``.

If Jexus Manager detects this file, a default server called "IIS Express" is
automatically created and showed.

Add IIS Express From Custom Configuration File
----------------------------------------------
An IIS Express server can be easily created from a custom configuration file.

#. Click "File | Connect to a Server…" menu item, and a wizard starts,

   .. image:: _static/add_server_types.png

#. Choose IIS Express Configuration File and click "Next" button.

#. Specify full path of the configuration file (.config) in the text box, or
   click "..." button to browse the file system,

   .. image:: _static/add_server_iis_express_file.png

#. Click Next button.

#. Give this connectioni a unique and meaningful name.

   .. image:: _static/add_server_name.png

#. Click "Finish" button.

Add IIS Express From Visual Studio 2015/2017 Solution File
----------------------------------------------------------
When you create a new web project in Visual Studio 2015/2017, the IDE adds a
custom IIS Express configuration file to the project folder at
``($SolutionDir)\.vs\config\applicationHost.config``.

.. note:: This file (and the ``.vs`` folder) is hidden by default in Windows
   Explorer.

   IIS Express custom configuration is documented in `this blog post <http://blogs.msdn.com/b/webdev/archive/2015/04/29/new-asp-net-features-and-fixes-in-visual-studio-2015-rc.aspx>`_ .

JetBrains Rider uses a similar approach, and it puts the configuration file at
``($SolutionDir)\.idea\config\applicationHost.config``.

.. note:: This file (and the ``.idea`` folder) is hidden by default in Windows
   Explorer.

Jexus Manager allows you to add such a solution file as a new IIS Express
server (so it automatically locates and reads the hidden configuration files).

#. Click "File | Connect to a Server…" menu item, and a wizard starts,

   .. image:: _static/add_server_types.png

#. Choose Visual Studio IIS Express Configuration File and click "Next" button.

#. Specify full path of the solution file (.sln) in the text box, or click
   "..." button to browse the file system,

   .. image:: _static/add_server_vs.png

#. Specify which custom configuration file to use, from Visual Studio or Rider.

   .. image:: _static/rider.png
  
   Jexus Manager takes care of the rest to manage web sites and applications.

   .. note:: For new projects/solutions, please debug/run them at least once
      in Visual Studio, so that IIS Express configuration file can be added.

#. Click Next button.

#. Give this connection a unique and meaningful name.

   .. image:: _static/add_server_name.png

#. Click "Finish" button.

Next Step
---------
Once a server is added, sites and applications can be managed by choosing one
of the categories in the middle panel.

.. image:: /_static/jexus.png

.. note:: If the server node is not yet expanded for management, double click
   the node so that Jexus Manager tries to load its configuration.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/support/known-issues`
- :doc:`/support/troubleshooting`
