Renew mailserver certificate
............................

The mailserver does not pick up a new let's encrypt certificate automatically, so we have to restart the mailserver sometimes.

#. Login to server
#. ``service postfix restart``
#. ``service dovecot restart``

If this does not work, check that the correct certificate is used in the dovecot and postfix configs. It might have changed to a new one after a server move where the old certificate was set to expire.
