PAT renewing
............

#. Login to github
#. Click on avatar -> Settings -> Developer Settings (bottom) -> Personal access tokens -> Tokens (classic)
#. Select correct PAT
#. Regenerate token
#. Set expiration date (30 days for normal token is probably good - should not be too long)
#. Copy PAT token (and save in password manager maybe)
#. Edit code to have something to push
#. Add and commit changes
#. ``git config --global credential.helper store``
#. Push and enter credentials

Add repo to github
..................

#. Login to github
#. Create repo with same name as locally
#. Edit code to have something to push
#. Add and commit changes
#. Copy link to repo from github
#. ``git remote add origin <repo>``
#. ``git push --set-upstream origin master``

Manually create and apply patches
.................................

Create last <n> number of patches from topmost commits with

``git format-patch -<n>``

Apply three way merge

``git am -3 < file.patch``

Resolve merge conflict

``git mergetool``

If the apply fails because it doesn't find sha1 number

``git remote add old_repo <url>``
``git fetch old_repo``

