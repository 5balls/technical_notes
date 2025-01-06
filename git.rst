git
---

Hooks
.....

git creates a default directory with hook examples in .git/hooks in the current directory. To create a hook copy / create a file with the same name but without the sample (or any) extension and make it executable.


For example to use the currently actively taskwarrior task as commit message, the file prepare-commit-msg could look like this:

.. code:: bash

    #!/bin/sh

    COMMIT_MSG_FILE=$1
    COMMIT_SOURCE=$2
    SHA1=$3

    task _get `task ids +ACTIVE`.description >> $COMMIT_MSG_FILE

