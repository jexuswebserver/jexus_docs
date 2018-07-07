Managing Local IIS Server
=========================

By `Lex Li`_

This page shows you how to manage the local IIS server in Jexus Manager.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
Jexus Manager is designed to be compatible with Microsoft IIS Manager.

Local IIS Server
----------------
When local IIS is installed, Windows creates its configuration file at
``%windir%\system32\inetsrv\config\applicationhost.config``.

If Jexus Manager detects this file, a default server with the machine name is
automatically created.

.. attention:: You have to run Jexus Manager as administrator so as to see the
   local IIS server node.

Next Step
---------
Once a server is there, sites and applications can be managed by choosing one
of the categories in the middle panel.

.. image:: /_static/jexus.png

.. note:: If the server node is not yet expanded for management, double click the node so that Jexus Manager tries to load its configuration.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/support/known-issues`
- :doc:`/support/troubleshooting`
