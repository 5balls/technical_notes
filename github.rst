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
