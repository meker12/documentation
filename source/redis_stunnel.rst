Stunnel for Redis
=================

The redis security model as designed to be utilized within trusted environments only, so this can make things challenging when trying to work with public hosting providers. fortunately there are a couple of workarounds available, one of which we'll be describing here.

What is stunnel?
~~~~~~~~~~~~~~~~

`stunnel <https://www.stunnel.org/index.html>`_ is a proxy designed to add TLS encryption functionality to existing clients and servers without any changes in the programs' code. What this means simply is that it's capable of wrapping unencrypted traffic with SSL to another server, but you have to set it up in front of your existing application.

As ObjectRocket Redis alreadys supports SSL on our end, you only need to set it up in front of your application to begin using SSL to send and receive traffic.

Installation & Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this example, we'll use Ubuntu:

.. code-block:: bash
    
    # apt-get install stunnel

From here you have a base install, and we can copy in the `necessary certificates <http://ssl.rackspaceclouddb.com/ca-cert.pem>`_:

.. code-block:: bash

    $ wget http://ssl.rackspaceclouddb.com/ca-cert.pem
    $ cp ca-cert.pem /etc/stunnel

Now we can create a configuration file for ObjectRocket:

.. code-block:: bash

    cafile = /etc/stunnel/ca-cert.pem
    delay = yes

    [objectrocket]
    client = yes
    accept = 127.0.0.1:6380
    connect = 0ecc8ec181ed479e961e0971e88be6.publb.rackspaceclouddb.com:6380

From here we can start stunnel using `service stunnel start`, and connect to redis as expected:

.. code-block:: bash

    $ redis-cli -h 0ecc8ec181ed479e961e0971e88be6.publb.rackspaceclouddb.com -p 6380 -a 6q7p4UmYgGQ2q6GWHhKCeEZXkg6rxzDMtu
    0ecc8ec181ed479e961e0971e88be6c4.publb.rackspaceclouddb.com:6380> ping
    PONG

Stunnel
~~~~~~~

If you need additional help setting up Stunnel, you can read their documentation `here <https://www.stunnel.org/howto.html>`_.
