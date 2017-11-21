
# Jons Notes

Some refs.

[Command Line Cheatsheet](http://blog.jasonmeridth.com/posts/postgresql-command-line-cheat-sheet/)    


#### Start Postgres on Mac OSX

```scala
// To have launchd start postgresql now and restart at login:
brew services start postgresql

// Or, if you don't want/need a background service you can just run:
pg_ctl -D /usr/local/var/postgres start
```

#### Stop Postgres on Mac OSX

```scala
pg_ctl -D /usr/local/var/postgres stop -s -m fast
```

#### Connect to postgres

```scala
psql postgres
```

#### Create Users

Note that `CREATE ROLE` is same as `CREATE USER`.

```scala
postgres=# CREATE ROLE scalaex_dev_user WITH LOGIN PASSWORD 'password';
CREATE ROLE

postgres=# CREATE ROLE scalaex_test_user WITH LOGIN PASSWORD 'password';
CREATE ROLE
```

#### Drop Roles (if you need to)

```scala
postgres=# DROP ROLE scalaex_dev_user;
DROP ROLE

postgres=# DROP ROLE scalaex_test_user;
DROP ROLE
```

#### Create DBs

```scala
postgres=# CREATE DATABASE scalaex_dev;
CREATE DATABASE

postgres=# CREATE DATABASE scalaex_test;
CREATE DATABASE
```

#### Drop DBs (if you need to)

```scala
postgres=# DROP DATABASE scalaex_dev;
DROP DATABASE

postgres=# DROP DATABASE scalaex_test;
DROP DATABASE
```

#### Grant priveleges to users

```scala
postgres=# GRANT ALL PRIVILEGES ON DATABASE scalaex_dev TO scalaex_dev_user;
GRANT

postgres=# GRANT ALL PRIVILEGES ON DATABASE scalaex_test TO scalaex_test_user;
GRANT
```

#### List DBs

```scala
postgres=# \l

                                       List of databases
     Name     |  Owner  | Encoding |   Collate   |    Ctype    |       Access privileges
--------------+---------+----------+-------------+-------------+-------------------------------
 postgres     | jonjack | UTF8     | en_GB.UTF-8 | en_GB.UTF-8 |
 scalaex_dev  | jonjack | UTF8     | en_GB.UTF-8 | en_GB.UTF-8 | =Tc/jonjack                  +
              |         |          |             |             | jonjack=CTc/jonjack          +
              |         |          |             |             | scalaex_dev_user=CTc/jonjack
 scalaex_test | jonjack | UTF8     | en_GB.UTF-8 | en_GB.UTF-8 | =Tc/jonjack                  +
              |         |          |             |             | jonjack=CTc/jonjack          +
              |         |          |             |             | scalaex_test_user=CTc/jonjack
```

#### List Users (Roles)

```scala
postgres=# \du

                                       List of roles
     Role name     |                         Attributes                         | Member of
-------------------+------------------------------------------------------------+-----------
 jonjack           | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
 scalaex_dev_user  |                                                            | {}
 scalaex_test_user |                                                            | {}
```

