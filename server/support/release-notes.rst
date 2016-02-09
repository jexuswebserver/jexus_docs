Release Notes
=============

By `Lex Li`_

This page shows you the release notes of Jexus web server. 

.. contents:: In this article:
  :local:
  :depth: 1
  
Version 5.8.0
-------------
Released on Dec 20, 2015

* Converted the core to be an asynchronous model.

Version 5.6.5
-------------
Released on Oct 11, 2015

* Fixed a bug that in rare cases IndexOutOfRangeException is thrown under high load.

Version 5.6.4
-------------
Released on May 30, 2015

* Fixed the bug that for FastCGI module port number appears in SERVER_NAME variable.
* Added log entries for reverse proxy module.
* Enhanced security protection to prevent cross site scripting via some special URL patterns.

Version 5.6.3
-------------
Released on Jan 4, 2015

* "X-Real-Host" header is added by Jexus when reverse proxy is enabled. This header contains HTTP host header from original requests.
* Added a feature so that Jexus automatically kills the process who listens to the ports in need.
* Optimized the strategy of web application loading. Switched from MultiDomainHost to SingleDomain.

Version 5.6.2
-------------
Released on Oct 12, 2014

* Fixed the bug that data lost in reverse proxy and FastCGI modules when PUT requests are being processed.
* Optimized ASP.NET thread pooling algorithm to achieve better throughput.

Version 5.6.1
-------------
Released on September 28, 2014

* Added OWIN support, and OWIN compliant frameworks such as NancyFX/SignalR are supported.
* Added HTTP 100 support when client side sends "Expect: 100-continue".
* Add chunked transfer encoding support to FastCGI module.

Version 5.5.3
-------------
Released on July 30, 2014

* Fixed the bug that leads to incomplete log files.
* Added a dedicated thread pool for FastCGI module to boost concurrency.

Version 5.5
-----------
Released on Jan 12, 2014

* Fixed "ASP.NET log entry might be incomplete" bug in logging.
* Added two settings in server configuration, httpd.MaxTotalMemory and httpd.MaxCpuTime.
* Added app_offline.htm support.

Version 5.4.4
-------------
Released on Oct 1, 2013

* Maximum number of worker processes is increased to [number of CPU cores] + 1 (still need to be <= 8).
* Maximum connections are now dynamically adjusted to avoid file descriptor exhaustion.
* Enabled TCPDEFERACCEPT option at TCP layer.
* Fixed "cannot find all hang worker processes" bug in application pool ping.
* Fixed "Range: byte=0-x is not properly processed" bug in Range header processing.
* Fixed "ASP.NET module cannot get external port number in NAT setup where external and internal port numbers differ" bug.

Version 5.4
-----------
Released on July 1, 2013

* Added application pool ping support.
* Added a new option to change socket listener binding from default to a certain IP address.
* Added a new option to control IP address whitelist.

Version 5.3
-----------
Released on May 11, 2013

* Fixed "Chinese characters in request path or query string can not be resolved correctly" bug in reverse proxy module.
* Fixed "pathinfo is lost" bug.
* Improved HTTPS support.
* (Breaking) ASP.NET State Service is now incorporated into Jexus master service process to simplify management;
* (Breaking) Added a single command "jws" to replace individual commands like "jws.start", "jws.stop".
* Core thread pool is optimized.

Version 5.2
-----------
Released on Jan 21, 2013

* FastCGI and reverse proxy modules now support multiple cookies.
* Added chunked transfer encoding support.
* Improved support for files with Chinese names mangled on Linux after copying from Windows.
* ASP.NET module now has OPTIONS/PUT/DELETE verbs enabled to support Web API projects.
* Improved data transmission method used in application pool control and cross app domain communication. Boosted static file performance by 5% and ASP.NET by 40%.
* Other bug fixes.

Version 5.1
-----------
Released on Sept 19, 2013

* Added FastCGI support.
* Improved overall performance.

Related Resources
-----------------

- :doc:`/getting-started/install`