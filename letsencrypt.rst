Renew mailserver certificate
............................

The mailserver does not pick up a new let's encrypt certificate automatically, so we have to restart the mailserver sometimes.

#. Login to server
#. ``service postfix restart``
#. ``service dovecot restart``
