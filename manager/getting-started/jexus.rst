Managing Remote Jexus Server
============================

By `Lex Li`_

This page shows you how to manage the Jexus web server remotely in Jexus
Manager.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
Jexus Manager is designed to be compatible with Jexus web server.

Jexus Web Server and Remote Services
------------------------------------
Jexus web server is a Linux based web server to run ASP.NET/PHP applications.

More information about it can be found
`here <http://server.jexusmanager.com/>`_ .

To enable Jexus Manager to connect and manage Jexus web server, a server side
component, aka Remote Services, must be installed and configured in advance.

More information can be found at
`GitHub <https://github.com/jexuswebserver/RemoteServices/releases>`_ .

After configuring the Remote Services, Jexus Manager can be used to manage the
remote server.

Next Step
---------
Once a server is there, sites and applications can be managed by choosing one
of the categories in the middle panel.

.. image:: /_static/jexus.png

.. note:: If the server node is not yet expanded for management, double click
   the node so that Jexus Manager tries to load its configuration.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/support/known-issues`
- :doc:`/support/troubleshooting`
