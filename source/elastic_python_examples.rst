Python Client Examples
======================

`Elasticsearch-py <https://elasticsearch-py.readthedocs.org>`_ is the recommended Python client for working with Elasticsearch.

Connecting 
------------

HTTP:
~~~~~~

.. code-block:: python

  from elasticsearch import Elasticsearch

  es = Elasticsearch(
      ['iad1-10202-0.es.objectrocket.com', 'iad1-10202-1.es.objectrocket.com', 'iad1-10202-2.es.objectrocket.com', 'iad1-10202-3.es.objectrocket.com'],
      http_auth=('user', 'pass'),
      port=10202,
  )
  
  print(es.info())

HTTPS:
~~~~~~~

.. code-block:: python

  from elasticsearch import Elasticsearch
  import certifi
  
  es = Elasticsearch(
      ['iad1-10202-0.es.objectrocket.com', 'iad1-10202-1.es.objectrocket.com', 'iad1-10202-2.es.objectrocket.com', 'iad1-10202-3.es.objectrocket.com'],
      http_auth=('user', 'pass'),
      port=20202,
      use_ssl=True,
      verify_certs=True,
      ca_certs=certifi.where(),
  )

Index a document
-----------------

.. code-block:: python

  es.index(index='test_index', doc_type='post', id=1, body={
    'author': 'John Doe',
    'blog': 'Learning Elasticsearch',
    'title': 'Using Python with Elasticsearch',
    'tags': ['python', 'elasticsearch', 'tips'],
  })


Get a document
---------------

.. code-block:: python

  es.get(index='test_index', id='1')
  

Search (DSL)
-----------------------

.. code-block:: python

  es.search(index='test_index', body={
    'query': {
      'match': {
        'title': 'Python',
       }
    }
  })

Delete a document
-----------------
.. code-block:: python

  es.delete(index='test_index', doc_type='post', id=1)

