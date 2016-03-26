Local IIS Instance
==================

By `Lex Li`_

This page shows you how to use Jexus Manager to manage local IIS instance.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
There are several issues with IIS Manager that you might not be able to use it to troubleshoot IIS configuration issues,

* IIS Manager strictly requires administrator permissions.
* Some file errors will trigger an error dialog (or 500.19 error page) that tells nothing useful.

.. image:: _static/iis_manager_error.png

Jexus Manager Benefits
----------------------
Jexus Manager can run as a normal user to navigate the settings, and its exception dialog provides the same or even better 
error message when an error is detected.

.. image:: _static/jexus_manager_error.png

.. note:: Jexus Manager current only provides read-only access to local IIS instance. No change in Jexus Manager is saved to IIS configuration file. Read-write access will be added in a future build.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
