Self-Signed Certificate Generation
==================================

By `Lex Li`_

This page shows you how to use Jexus Manager to generate self-signed certificates.

.. contents:: In this article:
  :local:
  :depth: 1

Background
----------
Before setting HTTPS bindings, it is very important to configure server certificates ahead. 

.. image:: _static/https_binding.png

Self-signed certificates are usually used during testing.

Self-Signed Certificate Wizard
------------------------------
In Jexus Manager, the self-signed certificate wizard can be opened as below,

#. Choose a server node in the Connections panel.
#. In the middle panel, click Server Certificates icon to open the management page.
#. Under Actions panel, click "Generate Self-Signed Certificate..." menu item.

.. image:: _static/self_signed.png

Fill in the necessary information in this wizard page, and then click OK. Jexus Manager will generate a new certificate and install it to the desired store.

Related Resources
-----------------

- :doc:`/getting-started/install`
- :doc:`/getting-started/features`
- :doc:`/tutorials/https-binding`
- :doc:`/tutorials/inplace-elevation`
- :doc:`/tutorials/ssl-diagnostics`