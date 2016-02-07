Automated Compaction Guide
==============================

This guide will walk you through getting automated compactions setup for your instance.  Feel free to follow the corresponding links if you'd like more details on understanding `MongoDB space usage <http://objectrocket.com/blog/how-to/understanding-mongodb-space-usage>`_ or if you'd like a more behind the scences look at our `automated compaction process <http://objectrocket.com/blog/company/automated-online-compaction>`_.

What is a Compaction?
----------------------
A compaction is a two phase process during which your shard members (1 Primary and 2 Secondaries) are compacted behind the scenes, one at a time.  During the first phase, your secondaries are compacted. To move from phase one to phase two a stepdown needs to happen on the primary. A stepdown is a graceful election of a new shard primary which takes 5-15 seconds, during which writes cannot take place. Most modern MongoDB drivers handle this type of operation gracefully, but in some rare cases an application restart may be required to clear stale connections. 

This being the case, we recommend that you schedule your stepdowns during non-peak hours. Once stepdown is completed, a compaction of the former primary occurs, thus compacting the whole instance.

Understanding the Stepdown Window Pane 
---------------------------------------

Once you select your MongoDB instance from the ObjectRocket UI and select the Settings button, you will be able to find the following section:

.. image:: images/compaction_pane.png
	:align: center

* Stepdown Scheduled: Is an on/off switch to ensure that stepdowns can or cannot occur (Recommendation: Enable).
* Stepdown Window (UTC): Is the timeframe that your instance is allowed to begin compacting secondaries and/or stepdown the primary.  There is a minimum of 15 minutes to allow for oplog differences between members (Recommended: Enable, and set for 30min to 1hr if possible.)
* Enable Weekly Stepdown: Allows stepdowns to occur during the Stepdown Window (Recommended: Enable).
* Enable Weekly Compaction: Allows your instance to perform automated compactions during the specified Stepdown Window (Recommendation: Enable).

.. image:: images/compaction_pane_example.png
	:align: center

If you have any further questions about compactions or stepdowns feel free to let us know by sending a ticket to `support@objectrocket.com <mailto:support@objectrocket.com>`_!  
