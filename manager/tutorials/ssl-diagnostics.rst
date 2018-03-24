SSL Diagnostics
===============

By `Lex Li`_

This page shows you how to use SSL Diagnostics.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
IIS 6 used to have a great suite of troubleshooting tools. One of them was for SSL related diagnostics, called
`SSL Diagnostics (SSL Diag or SSLDiag for short) <https://technet.microsoft.com/en-us/library/cc780913(v=ws.10).aspx>`_
.

As SSLDiag was designed for IIS 6 and relied on IIS ADSI API (which is now
obsolete), this tool was not made available for IIS 7 and above.

Of course you can use the IIS 6 version if you enable IIS 6 Compatibility
component on IIS 7 and above, but it would be less convenient.

A Microsoft employee Vijayshinva Karnure developed a newer version that relied
only on IIS 7+ new API, and `released it on IIS.net <https://www.iis.net/downloads/community/2009/09/ssl-diagnostics-tool-for-iis-7>`_ .

It works for all IIS versions (up to 10), but it does not work for IIS Express.

The Built-in SSL Diagnostics in Jexus Manager
---------------------------------------------
For web servers opened in Jexus Manager, there is an action called SSL
Diagnostics showed.

.. image:: _static/ssl_diag.png

A report is generated when "Generate Report" button is clicked.

.. image:: _static/ssl_report.png

Typical things analyzed by SSL Diagnostics,

* SNI or IP based mappings in Windows HTTP API.
* Certificate related,
   * Signature algorithm (SHA-1 is obsolete).
   * Validity check (expired or not).
   * Subject Alternative Name extension (should present as browsers require).
   * Private key availability.
   * Chain verification.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/tutorials/https-binding`
- :doc:`/tutorials/inplace-elevation`
- :doc:`/tutorials/self-signed`
