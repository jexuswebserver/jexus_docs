Troubleshooting
===============

By `Lex Li`_

This page shows you how to troubleshoot common issues. 

.. contents:: In this article:
  :local:
  :depth: 1

How to troubleshoot client/server connectivity?
-----------------------------------------------
Answer: First please follow server component installation steps to review if you have executed every steps.

Second, check the issues step by step,

Certificate
^^^^^^^^^^^
Assume that we register the certificate to port 8088. Run the following command,

.. code-block:: shell

  sudo httpcfg -list

You must see the port and certificate thumbprint listed which is similar to below,

.. code-block:: shell

  Port: 8088 Thumbprint: 38A913B07B138730DC9B7B13DC4F51310ADC6C93 

Otherwise, the certificate was not properly registered.

Service Address
^^^^^^^^^^^^^^^
Assume that we are using a machine whose IP address if ``192.168.18.129``. Run the following command,

.. code-block:: shell

  ifconfig

You can see the "inet address" for each network adapters, and learn which are the valid IP addresses you can use in service address.

The port number used in service address must have a server certificate registered. Otherwise, the client cannot make an HTTPS connection to the server side.

Firewall
^^^^^^^^
Linux distributions normally come with built-in firewall products. So exceptions for the port chosen for Jexus Manager server component must be made. You have 
to refer to the corresponding distro or firewall manuals to learn how to create such firewall exceptions. If you choose port ``8088``, then TCP access to that port 
must be registered as an exception.

If the client/server connection goes through the Internet, you should be even more caution that sometimes the connection can be blocked unexpectedly. Try to use 
another port number (such as ``12345``) and try again. 

REST Test
^^^^^^^^^
The service address (such as https://192.168.18.129:8088) and user credentials (jexus|lextudio.com) can be used to test out the server component availability via 
curl or WFetch.

* URL: https://192.168.18.129:8088/api/server
* Verb: GET
* Header: "X-HTTP-Authorization: jexus|lextudio.com"

The server should reply with 200 if configuration is correct.

What if client side reports connection failure and the error message is not clear enough?
-----------------------------------------------------------------------------------------
Answer: JexusManager.exe writes the exception details to a file named "debug". Open it and you will see the information.

For Jexus Manager 2.0 and above, this debug log file is located at "My Documents\Jexus Manager\temp\debug".

What is the cause of "System.Reflection.TargetInvocationException" when starting/stopping Jexus Manager Remote Services?
------------------------------------------------------------------------------------------------------------------------
Answer: If the exception details match below, then please make sure you pass a valid service address to RemoteServicesHost.exe.

.. code-block:: shell

  Unhandled Exception:
  System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Net.Sockets.SocketException: The requested address is not valid in this context
    at System.Net.Sockets.Socket.Bind (System.Net.EndPoint local_end) [0x00000] in <filename unknown>:0 
    at System.Net.EndPointListener..ctor (System.Net.IPAddress addr, Int32 port, Boolean secure) [0x00000] in <filename unknown>:0 
    at System.Net.EndPointManager.GetEPListener (System.String host, Int32 port, System.Net.HttpListener listener, Boolean secure) [0x00000] in <filename unknown>:0 
    at System.Net.EndPointManager.AddPrefixInternal (System.String p, System.Net.HttpListener listener) [0x00000] in <filename unknown>:0 
    at System.Net.EndPointManager.AddListener (System.Net.HttpListener listener) [0x00000] in <filename unknown>:0 
