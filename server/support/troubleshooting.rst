Troubleshooting
===============

By `Lex Li`_

This page shows you how to troubleshoot common issues. 

.. contents:: In this article:
  :local:
  :depth: 1

What is the cause of "System.Exception: Create work process error" when starting Jexus?
---------------------------------------------------------------------------------------
Answer: The detailed exception message is as below,

.. code-block:: shell

  System.Exception: Create work process error.
    at A.g.A (Int32 A, System.Collections.Generic.List`1 a, System.String B, Int32 b, Boolean C, Boolean c, Int32 D, Int32 d) [0x00000] in <filename unknown>:0
    at A.G.A (System.String[] A) [0x00000] in <filename unknown>:0
  05-02 16:22:51: Create httpd process failed:

Normally this is caused by corrupt Mono installation. Thus, you need to use official Mono packages from the distribution package repository, or build without any error from source code.

How to use ASP.NET session service?
-----------------------------------
Answer: Jexus already bundles an ASP.NET session service which monitors port 42424. So simply modify your web.config to point to this port and you can get it done.

How to reset Jexus?
-------------------
Answer: The following commands reset Jexus worker processes and web server,

.. code-block:: shell

  sudo killall -9 mono
  sudo mono jws.exe

Unfortunately other Mono processes are also closed.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/upgrade`
