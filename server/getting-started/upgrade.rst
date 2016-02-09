Upgrade Jexus Web Server
========================

By `Lex Li`_

This page shows you how to upgrade Jexus web server on a Linux machine. 

.. contents:: In this article:
  :local:
  :depth: 1

Download and Unpack Jexus Files
-------------------------------

.. code-block:: shell

  wget http://www.linuxdot.net/down/jexus-x.y.z.tar.gz
  tar -zxvf jexus-x.y.z.tar.gz

Jexus binary package is downloaded from its official site, and extracted to a folder named “jexus-x.y.z″ after this step.

Stop Current Jexus Server
-------------------------

.. code-block:: shell

  cd /usr/jexus
  sudo ./jws stop

Assume the previous release was installed at /usr/jexus, we stop the service. If Jexus 5.3 was there, use "sudo ./jws.stop" instead of "sudo ./jws stop".

Copy New Files
--------------

.. code-block:: shell

  cd ~/jexus-x.y.z
  sudo ./upgrade

Now let’s go back to the extracted folder and upgrade necessary files to /usr/jexus.

Fix Startup Commands
--------------------

.. code-block:: shell

  sudo vi /etc/rc.local

Press i on keyboard to enter edit mode.

If previous start command “/usr/jexus/jws.start” exists, replace it with “/usr/jexus/jws start”.

Remove “/usr/jexus/state.start” if it presents.

Press Esc on keyboard to exit edit mode.

Type :wq and press Enter on keyboard to exit vi.

Here we remove the old entries, and use a new entry to start Jexus at startup.

Start Jexus HTTP Service
------------------------

.. code-block:: shell

  cd /usr/jexus 
  sudo ./jws start

Related Resources
-----------------

- :doc:`/getting-started/install`
