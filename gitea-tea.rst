cli tool tea for accessing gitea
--------------------------------

Cheat-Sheet
...........

Show repos:

.. code::

   tea repos

Create a new repo (not documented?):

.. code::

   tea repos create --name <reponame> --desc <description> --private

And push existing repo to it (same as github):

#. ``git remote add origin <repo>``
#. ``git push --set-upstream origin master``

Create a new login (also with a token):

.. code:: shell

   tea login add


Installation
............

No debian package in current stable (2024-12-04).

Installation from source does not work for current git, but does work for 0.9.2, latest tagged version after running

.. code:: shell

   go mod vendor


which downloads a bunch of go stuff (something like 400MB in my case).

.. code:: shell

   make

will build it just fine and :code:`make install` will install it into :code:`~/go/bin` so be sure to add this to your PATH.
