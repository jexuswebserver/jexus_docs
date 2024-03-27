SSL Diagnostics for IIS/IIS Express
===================================

By `Lex Li`_

This page shows you how to use SSL Diagnostics.

Background
----------
There were either official or unofficial tools from Microsoft called SSL
Diagnostics.

IIS 6 used to have a great suite of troubleshooting tools. One of them was for
SSL related diagnostics, called `SSL Diagnostics (SSL Diag or SSLDiag for
short) <https://technet.microsoft.com/library/cc780913(v=ws.10).aspx>`_ .
As it was designed for IIS 6 and relies on IIS ADSI API (which is obsolete),
this tool was not made available for IIS 7 and above.

.. note:: Of course you can use the IIS 6 version if you enable IIS 6
   Compatibility component on IIS 7 and above, but it would be less convenient.

Later, a Microsoft employee Vijayshinva Karnure developed a newer version that
relied only on IIS 7+ new API, and `released it on IIS.net
<https://www.iis.net/downloads/community/2009/09/ssl-diagnostics-tool-for-iis-7>`_ .
It works for all IIS versions (up to 10), but it does not work for IIS Express.

.. important:: The previous tools were designed without SHA-2 and recent
   SSL/TLS best practices in mind. Their reports can simply miss recent
   warnings on obsolete SHA-1 certificates and obsolete protocols like SSL 3.0.

So what if you want a modern tool to troubleshoot SSL/TLS issues on IIS and
especially IIS Express? Jexus Manager fills the gaps.

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

This SSL Diagnostics tool is updated often to include more checks on recent SSL
/TLS best practices.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/tutorials/https-binding`
- :doc:`/tutorials/binding-diagnostics`
- :doc:`/tutorials/inplace-elevation`
- :doc:`/tutorials/self-signed`
