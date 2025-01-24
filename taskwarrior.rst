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

Renew taskd certificates (Debian)
.................................

Disable taskd service by

.. code:: bash

   systemctl stop taskd

In /usr/share/taskd/pki call generate script and copy the .pem files to


.. code:: bash

   cp client.cert.pem client.key.pem server.cert.pem server.key.pem server.crl.pem ca.cert.pem /var/lib/taskd/

Call

.. code:: bash

   ./generate.client first_last

and copy

.. code:: bash

   cp first_last.key.pem first_last.cert.pem /var/lib/taskd/

Finally enable the service again:

.. code:: bash

   systemctl start taskd


Copy ca.cert.pem and first_last files to the client.
