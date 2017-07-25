Known Issues
============

By `Lex Li`_

This page shows you what are the known issues. 

.. contents:: In this article:
  :local:
  :depth: 1

IIS Express
-----------

Supported Features
^^^^^^^^^^^^^^^^^^
#. Read-write access to IIS Express configuration.
#. Basic support for server/site/app/virtual directory/physical directory settings.
#. Basic support for adding/editing/deleting pool/site/app/virtual directory. 
#. Sites can be started and browsed.
#. Many more settings are now supported and editable, such as Default Document, URL Rewrite, Authentication and so on.
#. Server Certificate feature is completed. Elevation will be automatically requested.
#. ASP.NET Impersonation support is added.
#. Self signed certificate generation supports more parameters (such as CN, bit length, hashing method)
#. IIS 7/8/10 Express seamless support by automatically adapting to their unique schema files.
#. Add a server level HTTP API page to view IP and SNI based certificate bindings.
#. Detailed error message is displayed when a site fails to start.
#. Globle config file is loaded by default, while custom config files can be added via "File | Connect to a Server..." menu item. Simply choose "IIS Express Configuration File" and follow the wizard.
#. Include SSL Diagnostics.

Known issues
^^^^^^^^^^^^
* Many editing menu items/buttons currently raise exceptions or do nothing. (Will fix in Beta 4)
* Sites in folders with read-only access can be modified but changes cannot be saved (and might lead to various issues). (Will fix in Beta 4)
* More ASP.NET related settings. (Coming in Beta 4)
* IIS 7 Express always uses 32 bit processes. (original limitation from Microsoft)
* ProcessorAction enum is reset to default value if set to a value IIS 7 Express does not support. (original limitation from Microsoft)
* Visual Studio integration is under investigation. Changing a site's settings (such as bindings) might lead to problems when opening its project file in VS.
* Start/stop a site can take a few seconds, due to the current design to health check on IIS Express process.

Local IIS
---------
Only local IIS installation is displayed and displayed in read-only mode. Any changes made will trigger exceptions (can be ignored safely). 

Read/write support is coming in a later build (very likely 3.0).

Note that this mode is provided for IIS troubleshooting and compatibility testing.

Jexus
-----
Both local/remote Jexus web servers are supported. Currently this functionality is being ported from 1.1 to 2.0 new design, so still experimental.

About how to connect to Jexus web server, please refer to previous documentation on [release:121174].

Since Jexus only has a few options (compared to IIS/IIS Express), only certain changes in Jexus Manager affects the configuration files on Jexus side. 
More info can be found in [url:this article|http://jexuswebserver.readthedocs.io/en/latest/tutorials/configuration.html]. The "Jexus Specific" page at each level 
provides access to those settings that have no IIS equivalent.

New Issues
----------
Issues can be reported at `GitHub <https://github.com/jexuswebserver/jexusmanager/issues>`_ .

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/support/troubleshooting`
