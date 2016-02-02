Node.js Client Examples
========================

Installation
------------

Installing the `Node.js client <https://www.npmjs.com/package/elasticsearch>`_ is simple, using the usual npm install procedure:

::

  npm install elasticsearch

Connecting
------------
The example below shows the connection settings using ``HTTPS``.  If you prefer to use ``HTTP``, you only need to change ``protocol: 'http'`` and ``port: 10202``. 

.. code-block:: javascript

  var elasticsearch = require('elasticsearch');
  var client = new elasticsearch.Client({
    hosts: [
      {
        protocol: 'https',
        host: 'iad1-10202-0.es.objectrocket.com',
        port: 20202,
        auth: 'user:pass'
      },
      {
        protocol: 'https',
        host: 'iad1-10202-1.es.objectrocket.com',
        port: 20202,
        auth: 'user:pass'
      },
      {
        protocol: 'https',
        host: 'iad1-10202-2.es.objectrocket.com',
        port: 20202,
        auth: 'user:pass'
      },
      {
        protocol: 'https',
        host: 'iad1-10202-2.es.objectrocket.com',
        port: 20202,
        auth: 'user:pass'
      }
    ]
  });

  client.ping({
    requestTimeout: 30000,
    hello: "elasticsearch"
  }, function (error) {
    if (error) {
      console.error('Cluster is not available !');
    } else {
      console.log('All clear!');
    }
  });


Index a document
-----------------

.. code-block:: javascript

  client.index({
    index: 'example_index',
    type: 'posts',
    id: '1',
    body: {
      user: 'me',
      post_date: new Date(),
      message: 'Hello World!'
    },
    refresh: true
  });

Search (DSL)
-------------

.. code-block:: javascript

  client.search({
    index: 'example_index',
    type: 'posts',
    body: {
      query: {
        match: {
          body: 'Hello World'
        }
      }
    }
  });

Delete a document
------------------

.. code-block:: javascript

  client.delete({
    index: 'example_index',
    type: 'posts',
    id: '1',
  })

