Pretix update
=============

Backup
------

.. code:: sh

   su postgres
   pg_dump pretix > <datum>_backup.sql


Update
------

Check update notes for any possible issues:

https://docs.pretix.eu/en/latest/admin/updates.html

and follow steps on

https://docs.pretix.eu/en/latest/admin/installation/manual_smallscale.html#manual-updates

Apache configuration
--------------------

Working Apache setup

.. code:: apache

   <VirtualHost *:443>
       LogLevel info
       ServerAdmin <email>
       ServerName pretix.<url>
       ErrorLog ${APACHE_LOG_DIR}/error_pretix.log
       CustomLog ${APACHE_LOG_DIR}/access_pretix.log combined
       Include /etc/letsencrypt/options-ssl-apache.conf
       AssignUserId pretix pretix
       RequestHeader append Referrer-Policy same-origin
       RequestHeader append X-Content-Type-Options nosniff
       SSLProxyEngine on
       ProxyPreserveHost Off
       SSLProxyVerify none
       SSLProxyCheckPeerName Off
       ProxyRequests Off
       SSLProxyCheckPeerCN off
       DocumentRoot /var/pretix/data/media/
       RequestHeader set X-Forwarded-Proto https;
       RequestHeader set Host $http_host;
       ProxyPass "/static" "!"
       ProxyPass / http://localhost:8345/
       ProxyPassReverse / http://localhost:8345/
       ProxyAddHeaders On
       <Location /media/>
           Alias /var/pretix/data/media/
           ExpiresDefault "access plus 7 days"
       </Location>
       <Location /media/cachedfiles>
           Require all denied
       </Location>
       <Location /media/invoices>
           Require all denied
       </Location>
       <Location "/static">
           AliasPreservePath on
           Alias "/var/pretix/venv/lib/python3.11/site-packages/pretix/static.dist"
       </Location>
       <Directory "/var/pretix/venv/lib/python3.11/site-packages/pretix/static.dist">
           Require all granted
       </Directory>
       ServerAlias www.pretix.<url>
       SSLCertificateFile /etc/letsencrypt/live/<url>/fullchain.pem
       SSLCertificateKeyFile /etc/letsencrypt/live/<url>/privkey.pem
   </VirtualHost>


Lessons learned:

:code:`ProxyPass` overwrites :code:`Location` entries so any request send to static was sent to the localhost port and django / gunicorn. While this worked for previous pretix installations this does not work anymore now. The additional :code:`ProxyPass` line prevents this. Maybe this could also be prevented by putting :code:`ProxyPass` itself into a :code:`Location` ?
