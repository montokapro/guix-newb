## Background

To contribute a package with a git reference you will need to validate the hash of the package. This process was a bit hidden in the documentation.

## Resolution

To generate the hash in your package you should run
```
git clone https://github.com/user/repo.git
git status
cd repo/
guix hash -rx .
```

Perhaps there is a better way to generate this through a guile script, though I haven't found it yet.
