IIS Express Specific
====================

By `Lex Li`_

This page shows you how IIS Express works differently from other web servers.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
IIS Express is a development server that behaves differently from full IIS.

Microsoft Documentation
-----------------------
Microsoft has listed several key differences in the article below,

http://www.iis.net/learn/extensions/introduction-to-iis-express/iis-express-overview

It might contain the key information but some users could not understand it easily.

Further Explanation
-------------------

Application Pools
^^^^^^^^^^^^^^^^^
Though IIS Express uses the same format of configuration file (``applicationHost.config``), and each web sites has an application pool assigned, it does not support 
application pool at all. Every time an IIS Express instance is launched, it always uses the current user's credentials, and ignore the identity setting in 
``applicationHost.config``.

As IIS Express is a single instance server, there is no application pool recycle either. You can manually stop and restart the process, but that's different from 
application pool recycle (which by default uses the overlapped mode).

This is what Microsoft means by saying "user launches and terminates sites".

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
