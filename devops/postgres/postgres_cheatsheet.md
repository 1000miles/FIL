# Postgres

## Unix

### Help

```bash
$ psql --help
```

### Create

#### Create a new user (pguser) who can create databases and roles

```bash
$ createuser -Pdr pguser
```

#### Create a new user (pguser) as user postgres

```bash
$ sudo -u postgres createuser -s pguser
```

#### Create new user via `psql` interface after login

```bash
# Login
[root@servername ~] \# su - postgres

# Create user and password
CREATE USER pguser PASSWORD 'password123';
```

```bash
# Login
[root@servername ~] \# su - postgres

# Create user, password, database and role
CREATE USER pguser PASSWORD 'password123' CREATEDB CREATEROLE CREATEUSER; # CREATEUSER is alias of CREATEROLE - difference: with CREATEUSER login is assumed by default
```

#### Create a user password

```bash
$ createuser -P password123
```

### Change

#### Change user (pguser) password via `psql` interface after login

```bash
# Login
[root@servername ~] \# su - postgres

# Change password of user pguser
ALTER USER pguser PASSWORD 'password321';
```

#### Change user (pguser) privileges interface after login

```bash
# Login
[root@servername ~] \# su - postgres

# Allow user pguser to create databases, roles and users
ALTER USER pguser CREATEDB CREATEROLE CREATEUSER;
```

#### Limit user (pguser) connection via `psql` interface after login

```bash
# Login
[root@servername ~] \# su - postgres

# Limit amount of connections for user (pguser)
ALTER USER pguser CONNECTION LIMIT 10;
```

### Delete

#### Delete user via `psql` interface after login
```bash
# Login
[root@servername ~] \# su - postgres

# Delete user (pguser)
DROP USER pguser;
```

#### Delete database via `psql` interface after login
```bash
# Login
[root@servername ~] \# su - postgres

# Delete user (pguser)
DROP USER pguser;

# Delete user from database and role
DROP DATABASE pguser;
```

#### Log into Postgres specifying database & user

```bash
$ psql -d database_name -U user_name

# when not being prompted for a password
$ psql -d database_name -U user_name -W
```

#### Log into a Postgres database on a server

```bash
$ psql -h host_name -d database_name -U user_name

# when not being prompted for a password
$ psql -h host_name -d database_name -U user_name -W
```
