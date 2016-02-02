PHP Driver Examples
===================

Connecting
-----------

.. code-block:: php

  <?php
  require 'vendor/autoload.php';
  
  $hosts = [
       'https://user:pass@iad1-10202-0.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-1.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-2.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-3.es.objectrocket.com:20202'
  ];
  
  $client = Elasticsearch\ClientBuilder::create()
                      ->setHosts($hosts)
                      ->build();
  
  $params = [
      'index' => 'myindex',
      'type' => 'mytype',
      'id' => '2'
  ];
  
  $response = $client->get($params);
  print_r($response);


Index a document
----------------

.. code-block:: php
 
  <?php
  require 'vendor/autoload.php';
  
  $hosts = [
       'https://user:pass@iad1-10202-0.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-1.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-2.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-3.es.objectrocket.com:20202'
  ];
  
  $client = Elasticsearch\ClientBuilder::create()
                      ->setHosts($hosts)
                      ->build();
  
  $params = [
      'index' => 'phpindex',
      'type' => 'my_type',
      'id' => '1',
      'body' => ['Description' => 'Hello World']
  ];
  
  $response = $client->index($params);
  print_r($response);

Get a document
---------------

.. code-block:: php

  <?php
  
  require 'vendor/autoload.php';
  
  $hosts = [
       'https://user:pass@iad1-10202-0.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-1.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-2.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-3.es.objectrocket.com:20202'
  ];
  
  $client = Elasticsearch\ClientBuilder::create()
                      ->setHosts($hosts)
                      ->build();
  
  $params = [
      'index' => 'phpindex',
      'type' => 'my_type',
      'id' => '1'
  ];
  
  $response = $client->get($params);
  print_r($response);

Search (DSL) 
-------------

.. code-block:: php

  <?php
  
  require 'vendor/autoload.php';
  
  $hosts = [
       'https://user:pass@iad1-10202-0.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-1.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-2.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-3.es.objectrocket.com:20202'
  ];
  
  $client = Elasticsearch\ClientBuilder::create()
                      ->setHosts($hosts)
                      ->build();
  
  $params = [
      'index' => 'phpindex',
      'type' => 'my_type',
      'body' => [
          'query' => [
              'match' => [
                  'Description' => 'Hello World',
              ]
          ]
      ]
  ];
  
  $response = $client->search($params);
  print_r($response);

Delete a document
------------------

.. code-block:: php

  <?php
  
  require 'vendor/autoload.php';
  
  $hosts = [
       'https://user:pass@iad1-10202-0.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-1.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-2.es.objectrocket.com:20202',
       'https://user:pass@iad1-10202-3.es.objectrocket.com:20202'
  ];
  
  $client = Elasticsearch\ClientBuilder::create()
                      ->setHosts($hosts)
                      ->build();
  
  $params = [
      'index' => 'phpindex',
      'type' => 'my_type',
      'id' => '1'
  ];
  
  $response = $client->delete($params);
  print_r($response);

