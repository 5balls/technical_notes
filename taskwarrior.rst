Taskwarrior
-----------

Create new context
..................

.. code:: bash

   task context define work +work or +freelance

UDA
...

.. code:: bash

   task config uda.estimate.type numeric
   task config uda.estimate.label Est

UDA's are IMO not correctly used when calculating urgency. IMO numerical values should be taken into account, currently taskwarrior only registers if there is an UDA defined and then uses 1.0 as factor instead of the value.
