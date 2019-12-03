## Background

After adding a postgres service to my operating system, I was unable to log in as the postgres user to run commands.

```
$ sudo su - postgres
Password: 
This account is currently not available.
$ cat /etc/passwd
postgres:x:123:456:PostgreSQL server user:/var/empty:/gnu/store/LONG-HASH/sbin/nologin
```

## Resolution

While it isn't possible to login as the postgres user, it is possible to run postgres under that user.

```
$ sudo -u postgres psql
Password: 
psql (10.10)
Type "help" for help.

postgres=# 
```

Note that when quitting, postgres command history is lost.

```
postgres=# \q
could not save history to file "/var/empty/.psql_history": No such file or directory
```
