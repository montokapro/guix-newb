terminal 1:
```
# This command will print out a command to run
sudo guix system container /home/steve/conf/system/postgres-config.scm

# For postgres to have access to a file system, you must run the command as root directly
sudo su - root

# This command will then print out another command to run
/gnu/store/abcdef01234567890abcdef-run-container
```

terminal 2:
```
# Run the following supplied command
sudo guix container exec 12345 /run/current-system/profile/bin/bash --login

# Start psql as the postgres user
sudo -u postgres psql
```
