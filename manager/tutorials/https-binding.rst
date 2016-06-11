HTTP API Page
=============

By `Lex Li`_

This page shows you how to use Jexus Manager HTTP API page to review IIS/IIS Express HTTPS bindings.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
If you have ever opened IIS 7+ configuration file (aka applicationHost.config), you probably know that an HTTPS binding of a site looks like below,

.. code-block:: xml

  <site name=”php” id=”8″>
    <bindings>
      <binding bindingInformation=”*:58000:localhost” protocol=”http” />
      <binding bindingInformation=”*:44300:localhost” protocol=”https” />
      <binding bindingInformation=”*:4431:localhost” protocol=”https” />
      <binding bindingInformation=”*:4431:lextudio.com” protocol=”https” />
    </bindings>
    <application path=”/” applicationPool=”32bit”>
      <virtualDirectory path=”/” physicalPath=”e:\test” />
    </application>
  </site>
  
It is rather strange that no certificate information is available here, while in Jexus Manager we can see the certificate selected for each bindings,

.. image:: _static/https_binding.png

So from where does Jexus Manager find the proper certificate?

IP Based Bindings
-----------------
If “Require Server Name Indication” is not checked, then this binding is not SNI enabled. It also means for this binding, the certificate is registered to the IP 
address + port number (in this example, ``0.0.0.0:44300``). Windows stores the certificate information in a private storage for http.sys to read, which can be 
queried via ``netsh http show sslcert``.

Jexus Manager features a new page to show the list,

.. image:: _static/http_api.png

It is very clear that the certificate mappings are here. 

.. image:: _static/https_ip_based.png

.. note:: IIS Express creates mappings for ``0.0.0.0:44300`` – ``0.0.0.0:44399`` during its installation, so that non administrators can bind HTTPS sites to such mappings.

Due to the limitation of such mappings, we know for a single IP end point, only a single certificate can be registered. That’s why when we attempt to host multiple 
HTTPS sites on a single IP end point we could only use a wildcard certificate or a UC certificate.

SNI Based Bindings
------------------
Starting from Windows 8/IIS 8 and above, we can create SNI based in addition to IP based bindings. This allows multiple certificates to be bind to a single IP end point.

.. image:: _static/https_sni.png

SNI based mapping for certificates is displayed under SNI tab. They are bind to host name + port number instead of IP end point + port number.

Such SNI based mappings are automatically created by Jexus Manager when you add SNI based bindings to web sites. They are also removed automatically when such bindings are removed from sites.

Reserved URLs
-------------
Reserved URLs are displayed under Reserved URL tab.

.. image:: _static/reserved_urls.png

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/tutorials/self-signed`
- :doc:`/tutorials/inplace-elevation`
- :doc:`/tutorials/ssl-diagnostics`
