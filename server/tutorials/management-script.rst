Management Script
=================

By `Lex Li`_

This page shows you how to use the management script. 

.. contents:: In this article:
  :local:
  :depth: 1

Starting from Jexus 5.3 the commands are merged into one Shell script, ``/usr/jexus/jws``.

This script provides the following functionality,

======================  =======================================================================================================================
Command	                Description
======================  =======================================================================================================================
jws start	              Start Jexus server.
jws start sitename	    Start a single web site. Note that sitename must match one of the configuration files under configuration directory.
jws restart	            Restart Jexus server.
jws restart site_name	  Restart a single web site.
jws stop	              Stop Jexus server.
jws stop site_name	    Stop a single web site.
jws regsvr	            Register Jexus assembly in GAC. Note that this is only required to be executed once during installation.
jws status	            Report Jexus runtime status.
jws -v	                Display Jexus version number.
======================  =======================================================================================================================

The script should be set to executable during installation. 

.. note:: The commands can only be executed by root.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/tutorials/configuration`
