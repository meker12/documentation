Parse Migration FAQ
===================

If you have any questions about anything in this FAQ, please don't hesitate to reach out to our `support team <mailto:support@objectrocket.com>`_

Why migrate from Parse?
~~~~~~~~~~~~~~~~~~~~~~~

On January 28th 2016 Parse announced they'd be shutting down their service, leaving quite a few customers questioning where they'd be moving. Luckily we've worked closely with Parse on creating a MongoDB instance on our platform in several different sizes to fit any Parse customers needs.

With their help we're able to transition any current customer from their platform to ours, and our support is ready to jump in if you have any questions about the process.

.. note::

    Until March 31st 2016, the first Parse instance you create will have 15% off for a full year. Sign up `here <https://objectrocket.com/parse>`_!

Why use ObjectRocket?
~~~~~~~~~~~~~~~~~~~~~

ObjectRocket's MongoDB-as-a-Service makes it easy to deploy and run your database by providing a production-ready instance instantly, tools to automate operations, and a fully staffed team of engineers and database administrators so you can focus on your application. Here are the highlights:

    * Our tech stack is optimized for MongoDB from the ground up, including PCIe flash-based infrastructure, high memory-to-disk ratios, and container-based virtualization.
    * We have the best MongoDB support specialists and DBA experts, bar none, and 24x7x365 support, whether you are a 5GB or a 5TB customer.
    * We have competitive pricing with price breaks as your data needs grow.
    * We offer both the standard uncompressed MongoDB storage engine, MMAPv1, and the newer compressed storage engine that shipped with MongoDB 3.0, WiredTiger. WiredTiger is most comparable to RocksDB, the compressed storage engine your app used at Parse.

What size instance should I choose?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This can be a difficult decision due to the compression available in RocksDB, which is the MongoDB storage engine that Parse used. Parse recommends choosing a plan that is 10x the size of the `Data storage` listed under `Analytics` in your Parse dashboard. The image below shows an example of what this looks like:

.. image:: images/parse_data_storage.png
   :align: center

Our Parse tuned instances are available in quite a few different sizes to fit your workload. Plan sizes are 20GB, 50GB, 100GB, 250GB, and 500GB for our compressed instances using WiredTiger. We also offer uncompressed MMAPv1 instances, designed for smaller deployments, available in 5GB and 20GB.

Where should I host my Parse API server?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



Parse Resources
~~~~~~~~~~~~~~~

    * Parse link 1
    * Parse link 2
    * Parse link 3

Why use ObjectRocket instead of self hosting?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
