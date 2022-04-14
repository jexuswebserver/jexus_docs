Binding Diagnostics for IIS/IIS Express
=======================================

By `Lex Li`_

This page shows you how to use Binding Diagnostics.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
IIS sites use bindings to determine what kind of incoming HTTP requests they
would handle.

For example, assume that there is only a default web site right now on IIS with
the following settings,

.. code-block:: xml

  <sites>
    <site name="first" id="8">
      <bindings>
        <binding bindingInformation="*:80:" protocol="http" />
      </bindings>
      <application path="/">
        <virtualDirectory path="/" physicalPath="e:\test1" />
      </application>
    </site>
  </sites>

The binding setting above ensures that all HTTP requests arriving at any of the
network adapters of this machine are sent to this web site by HTTP.sys.

And if we add a second site,

.. code-block:: xml

  <sites>
    <site name="first" id="8">
      <bindings>
        <binding bindingInformation="*:80:" protocol="http" />
      </bindings>
      <application path="/">
        <virtualDirectory path="/" physicalPath="e:\test1" />
      </application>
    </site>
    <site name="second" id="8">
      <bindings>
        <binding bindingInformation="*:80:lextudio.com" protocol="http" />
      </bindings>
      <application path="/">
        <virtualDirectory path="/" physicalPath="e:\test2" />
      </application>
    </site>
  </sites>

Then HTTP.sys forwards all HTTP requests with host header of "lextudio.com" to
the second site, while all other HTTP requests still go to the first site.

.. important:: To learn more about HTTPS bindings, check :doc:`/tutorials/https-binding`.

.. important:: If the site binding contains an IP address, make sure that IP
   address belongs to one of the network adapters of this machine. Using an
   invalid IP address only leads to an invalid binding.

.. warning:: Certain HTTP API settings such as Reserved URLs can have conflicts
   with site bindings. Check :doc:`/tutorials/https-binding`.

.. warning:: Excluded port ranges can also have conflicts with site bindings.
   Check `this KB article <https://support.microsoft.com/en-us/topic/you-cannot-exclude-ports-by-using-the-reservedports-registry-key-in-windows-server-2008-or-in-windows-server-2008-r2-a68373fd-9f64-4bde-9d68-c5eded74ea35>`_ .

.. note:: More information about site bindings can be found in 
   `this article <https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/sites/site/bindings/binding>`_. 

It requires experience to fully understand the concepts of site bindings and
how the HTTP request forwarding works especially when there are multiple sites
on the same machine. Without learning HTTP protocol itself and how
web browser/IIS work together, mistakes can be made easily.

That's why Jexus Manager includes a specific diagnostics tool in this area.

The Built-in Binding Diagnostics
--------------------------------
For a web site is opened in Jexus Manager, there is now a Binding Diagnostics
menu item showing in the Actions panel under Troubleshooting section,

.. image:: _static/bindings.png

Click this menu item and the Binding Diagnostics dialog shows. A report is
generated when "Generate Report" button is clicked.

.. image:: _static/binding_diag.png

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/tutorials/https-binding`
- :doc:`/tutorials/inplace-elevation`
- :doc:`/tutorials/self-signed`
- :doc:`/tutorials/ssl-diagnostics`
