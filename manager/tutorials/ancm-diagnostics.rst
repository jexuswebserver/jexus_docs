ASP.NET Core Diagnostics for IIS/IIS Express
============================================

By `Lex Li`_

This page shows you how to use ASP.NET Core Diagnostics.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
An ASP.NET Core web app requires certain setup before being executed properly.
However, the configuration steps are complex and critical settings might be
neglected, which leads to failed deployment and miserable issues such as 502.5,

* ASP.NET Core module is not installed.
* ASP.NET Core module version does not match the minimal version required by
  the web apps.
* Visual C++ 2015 runtime is not installed.
* Handler setting in ``web.config`` is invalid.
* In-process module has no access to the content folder.

A thorough diagnostics tool can reveal typical configuration mistakes and help
resolve them.

.. note:: Minimal ASP.NET Core module version required can be found in articles
   like `this <http://https://dotnet.microsoft.com/download/dotnet-core/2.2>`_.

The Built-in ASP.NET Core Diagnostics
-------------------------------------
For web sites opened in Jexus Manager, there is an action called ASP.NET Core
Diagnostics showed.

A report is generated when "Generate Report" button is clicked.

.. image:: _static/ancm_diag.png

Typical things analyzed by ASP.NET Core Diagnostics,

* ASP.NET Core module on IIS.
* Visual C++ 2015 runtime.
* Application pool (No Managed Code).
* Handler in web.config.
* Web app runtime version.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/tutorials/https-binding`
- :doc:`/tutorials/binding-diagnostics`
- :doc:`/tutorials/ssl-diagnostics`
- :doc:`/tutorials/inplace-elevation`
- :doc:`/tutorials/self-signed`
