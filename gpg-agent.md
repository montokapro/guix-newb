## Background

To contribute back to the Guix project you will need a GPG key. I found signing commits on GuixSD to be a bit tricky.

## Prerequisites

First, you'll need to install the gpg package:
```
guix install gnupg
```

Second, you'll need to create or import your gpg key.

## Resolution

When committing, I would get the error:
```
$ git commit
error: gpg failed to sign the data
fatal: failed to write commit object
```

This problem can be seen when invoking gpg directly.
```
$ echo "test" | gpg --clearsign
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

test
gpg: signing failed: No pinentry
gpg: [stdin]: clear-sign failed: No pinentry

```

Pinentry may already be installed for you. If not, `guix install pinentry` will do the trick.
```
$ pinentry
OK Pleased to meet you
$ which /run/current-system/profile/bin/pinentry
/run/current-system/profile/bin/pinentry
```

However, gpg cannot seem to find this dependency. To fix this I created `$HOME/.gnupg/gpg-agent.conf` and added the `pinentry-program` option to the file.
```
pinentry-program /run/current-system/profile/bin/pinentry
```

We then need to reload the gpg agent to read this new option.
```
$ gpg-connect-agent reloadagent /bye
```

Now `echo "test" | gpg --clearsign` correctly generates a pgp signature and we can sign our commits! I'm hoping for a better resolution in the future, but for now this is getting me by.
