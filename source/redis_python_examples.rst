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

SSL
---

Redis-py supports SSL encryption, provided you pass in the appropriate certificates.

.. code-block:: python

    import redis
    import sys

    if __name__ == "__main__":
      # Be sure to pip install redis and ssl.
      r = redis.Redis(host=sys.argv[1], ssl=True, port=6380, password=sys.argv[2], ssl_ca_certs=sys.argv[3])
      r.set('foo', 'bar')
      value = r.get('foo')
      print "This is the value of foo: " + value

With the above example, we can pass in the relevant values:

.. code-block:: bash

    python test.py 69edaf7ca8264890bf9e0ce919f90b.publb.rackspaceclouddb.com <authentication-password> ca-cert.pem
    This is the value of foo: bar

More Information
----------------

If you need additional help with redis-py, here are some useful links:

* `redis-py Official Documentation <https://github.com/andymccurdy/redis-py>`_

As always, if you have any questions, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_!
