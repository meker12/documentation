Python Connection Examples
==========================

.. |checkmark| unicode:: U+2713

The `redis-py <https://github.com/andymccurdy/redis-py>`_ package is the recommended client for Redis when using Python.

Installation
------------

Install redis-py at the command prompt if you haven't yet:

.. code-block:: bash

   $ pip install redis


Authentication
--------------

.. code-block:: bash

   >>> import redis
   >>> redis = redis.StrictRedis(host='#####.publb.rackspaceclouddb.com', port=6379, password='#####')

   >>> print(redis)
   >>> StrictRedis<ConnectionPool<Connection<host=#####.publb.rackspaceclouddb.com,port=6379,db=0>>>

C.R.U.D.
--------

Create, read, update and destroy are the four basic functions of persistent storage.

.. code-block:: python

   >>> redis.set("best_car_ever", "Tesla Model S")
   True

   >>> redis.get("best_car_ever")
   b'Tesla Model S'

   >>> redis.delete("best_car_ever")
   1

   >>> redis.get("best_car_ever")
   >>>

.. note::

   'del' is a reserved keyword in the Python syntax. Therefore redis-py uses 'delete' instead.

More Information
----------------

If you need additional help with redis-py, here are some useful links:

* `redis-py Official Documentation <https://github.com/andymccurdy/redis-py>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
