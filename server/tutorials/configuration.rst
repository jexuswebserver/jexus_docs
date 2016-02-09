Configuration System
====================

By `Lex Li`_

This page shows you what is the configuration system for Jexus web server. 

.. contents:: In this article:
  :local:
  :depth: 1

Server Configuration File
-------------------------
The configuration file, which contains most of Jexus settings, is located in Jexus installation folder (usually /usr/jexus) and named jws.conf.

Unlike IIS which uses XML to store settings, the Jexus settings are stored in key-value pair, for example

.. code-block:: ini

  SiteLogDir=log
  SiteConfigDir=siteconf

.. note:: Any change to server configuration only takes effect when Jexus is restarted.

The description of each settings is listed as below,

SiteConfigDir
^^^^^^^^^^^^^
* Mandatory
* The directory that holds web site configuration files. Relative paths to jws.exe can be used.
* No IIS equivalent

SiteLogDir
^^^^^^^^^^
* Mandatory
* The directory that holds the log files. Relative paths to jws.exe can be used.
* Equal to "system.applicationHost/log" section and "system.applicationHost/sites/site/logFile"

Runtime
^^^^^^^
* Optional
* Application pool ASP.NET runtime version. For example, ``Runtime=v4.0.30319`` or ``Runtime=v4.0``.
* Equal to "system.applicationHost/applicationPools/add/managedRuntimeVersion"

httpd.processes
^^^^^^^^^^^^^^^
* Optional
* Specifies the number of worker processes associated with the application pool. A value other than 1 indicates a Web garden. The default value is 1.
* Equal to "system.applicationHost/applicationPools/add/processModel/maxProcesses"

httpd.user
^^^^^^^^^^
* Optional
* Application pool identity. For example, ``httpd.user=www-data``. The default value is root.
* Equal to "system.applicationHost/applicationPools/add/processModel/identityType" and "system.applicationHost/applicationPools/add/processModel/userName"

httpd.MaxTotalMemory
^^^^^^^^^^^^^^^^^^^^
* Optional
* (5.5+) Specifies the maximum total physical memory (of MBytes) that all worker processes can consume before the pool starts to recycle worker processes. It ranges from 256 to 80% of maximum physical memory installed on the machine. The default is 0, where Jexus automatically adjusts the usage.
* No IIS equivalent

.. note:: Each worker process the minimum physical memory usage is 128-MBytes.

httpd.MaxCpuTime
^^^^^^^^^^^^^^^^
* Optional
* (5.5+) Specifies how much CPU resources (of seconds) can be consumed by a single worker process before being recycled by the pool. It ranges from 600 to 14400. The default value is 3600.
* No IIS equivalent

LLVM
^^^^
* Optional
* When a worker process is created, Jexus passes this flag to Mono. The default value is false.
* No IIS equivalent

certificatefile
^^^^^^^^^^^^^^^
* Optional
* File name of the server certificate file (in X.509 format). The default value is empty.
* No IIS equivalent

certificatekeyfile
^^^^^^^^^^^^^^^^^^
* Optional
* File name of the server certificate file private key (in PEM format). The default value is empty.
* No IIS equivalent

Website Configuration File
--------------------------
Jexus supports multiple web sites running on the same server. The web sites use individual bindings to distinguish from each other.

The web site configuration files must be saved in the configuration directory set in jws.conf (aka SiteConfigDir). The configuration file name is used as site name 
(site name is only used in Jexus commands), which should not contain spaces. Note that all files in configuration directory are treated as web site configuration files. 
Thus, don’t leave anything else there.

Note that any change to web site configuration only takes effect when the web site is restarted.

In default installation, a default web site is created. Its configuration file is ``/usr/jexus/siteconf/default``. Just like jws.conf, the web site configuration is also 
stored in key value pair, and the description of each settings is as below,

addr
^^^^
* Optional
* The web site IP address. Default is ``addr=0.0.0.0``. (no IP v6 support yet)
* Equal to "system.applicationHost/sites/site/binding"

port
^^^^
* Optional
* The port number used for this web site. Default is ``port=80``.
* Equal to "system.applicationHost/sites/site/binding"

hosts
^^^^^
* Optional
* The host header accepted by this web site. Default is ``hosts=*``, which means any host header is accepted. Wildcard is also supported, such as ``*.mysite.com``.
* Equal to "system.applicationHost/sites/site/binding"

root
^^^^
* Mandatory
* The directory mapping. The default is ``root=/ /var/www/default``, which maps physical directory ``/var/www/default`` that contains the web site contents to web site root.
* Equal to "system.applicationHost/sites/site/application/virtualDirectory"

indexes
^^^^^^^
* Optional
* Default document name list. For example, when ``indexes=index.aspx,index.htm`` is used, access to / will be resolved to index.aspx if it exists, and then index.htm if exists, and 404 if none of them exists. When this setting is not set, Jexus uses its built-in name list.
* Equal to "system.webServer/defaultDocument"

rewrite
^^^^^^^
* Optional
* URL rewrite rule. For example, ``rewrite=^/.+?.(asp|php|cgi)$ /404.html`` means any access to classic ASP/PHP/CGI pages is rewritten to ``/404.html``. To use multiple rules, use multiple lines of ``rewrite=``.
* Equal to "system.webServer/rewrite/rules"

denyfrom
^^^^^^^^
* Optional
* IP address restriction. For example, when ``denyfrom=111.222.111.*,1.1.1.1`` is used, access from the IP addreses are denied. Mask is also supported, such as ``denyfrom=192.168.1.0/255.255.255.0``.
* Equal to "system.webServer/security/ipSecurity"

allowfrom
^^^^^^^^^
* Optional
* IP address restriction. For example, when ``allowfrom=111.222.111.*,1.1.1.1`` is used, only access from the IP addresses are allowed. All other access is denied.
* Equal to "system.webServer/security/ipSecurity"

DenyDirs
^^^^^^^^
* Optional
* Hidden segments. When ``DenyDirs=bin,App_code`` is used, access to such URL paths is denied.
* Equal to "system.webServer/security/requestFiltering/hiddenSegments"

checkquery
^^^^^^^^^^
* Optional
* Query strings restriction. Jexus uses built-in logic to perform query safety check. The default is ``checkquery=true``. Note that by setting this to true, there is some impact on Jexus performance.
* No IIS equivalent

nofile
^^^^^^
* Optional
* NOFILE is a Jexus specific feature. It is similar to IIS custom error pages for 404. When ``nofile=/mvc/controller.aspx`` is used, access to non-existent files is redirected to ``/mvc/controller.aspx``.
* Equal to "system.webServer/httpErrors"

.. note:: The original URL is passed via X-Real-Uri server variable.

nolog
^^^^^
* Optional
* Logging flag. The default is ``nolog=false``. When set to true, Jexus stops generating log files for this web site.
* Equal to "system.applicationHost/sites/site/logFile"

keep_alive
^^^^^^^^^^
* Optional
* HTTP keep-alive flag. The default is ``keep_alive=true``.
* Equal to "system.webServer/httpProtocol/allowKeepAlive"

reproxy
^^^^^^^
* Optional
* Reverse proxy rule. When ``reproxy=/abc/ http://www.xxxx.com:890/abc/`` is used, requests on ``/abc/`` (source) will be redirected to ``http://www.xxxx.com:890/abc/`` (destination). The destination can be multiple, so that Jexus randomly picks one from them, which is similar to load balancing. For example, ``reproxy=/abc/ http://192.168.0.3/abc/,http://192.168.0.4/abc/``.
* No IIS equivalent

fastcgi.add
^^^^^^^^^^^
* Optional
* FastCGI rule. For TCP connections, typical setting is ``fastcgi.add=php,php3``
* No IIS equivalent

usegzip
^^^^^^^
* Optional
* GZip compression flag. The default is ``usegzip=true``.
* Equal to "system.webServer/urlCompression/doStaticCompression"

usehttps
^^^^^^^^
* Optional
* SSL flag. To enable HTTPS, this setting must be set to true, and port must be set to 443 at the same time. The default is ``usehttps=false``. The certificate configured at server level will be used.
* Equal to "system.applicationHost/sites/site/binding"

Application Configuration File
------------------------------
Applications under websites (IIS style applications) can be configured by creating websites, whose root points to the application path. Jexus Manager simplifies such application creation a lot, and also uses its own convention to set application configuration file names.

Virtual Directory Configuration File
------------------------------------
Jexus does not support IIS style virtual directories.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/tutorials/management-script`
