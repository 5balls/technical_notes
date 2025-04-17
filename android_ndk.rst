Install SDK and NDK for android
-------------------------------


Download and placement of cmdline tools
.......................................

Install the latest command line tools from googles webpage (the link changes and one has to accept the license conditions).

Place the files in

.. code::

   ~/.android_sdk/cmdline-tools/tools

and set the PATH in .bashrc accordingly:

.. code::

   export ANDROID_SDK_ROOT=$HOME/.android_sdk/cmdline-tools/
   export PATH=$PATH:$ANDROID_SDK_ROOT/tools/bin

Licenses
........

Run

.. code::

   sdkmanager --licenses

and accept (manually or automatically) all licenses. If it complains about not finding the correct directory for sdkmanager android has changed the filestructure again.

NDK
...

.. code::

   sdkmanager ndk-bundle

Platform tools
..............

.. code::

   sdkmanager platform-tools

tools
.....

.. code::

   sdkmanager tools


