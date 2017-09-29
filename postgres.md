# Postgres

## View things

#### Show all users 
``` \du ```

#### Show all databases
``` \l ```


## Users

Switch to postgres account

``` sudo -i -u postgres ```

Access postgres prompt

``` psql ```

Exit 

``` \q ```


### Create new role

When logged in as postgres account create new user

``` postgres@server:~$ createuser -P -s -e username ```


-P = password, 
-s = superuser, 
-e = echo


### Add an existing user to a database

``` GRANT permissions ON DATABASE dbname TO username; ```

for example

``` GRANT ALL PRIVILEGES ON DATABASE dbname TO username; ```


### Drop user
* but need to explicity drop any privileges associated with that user, also to move its ownership to other role

``` REASSIGN OWNED BY <olduser> TO <newuser> ```
``` DROP OWNED BY <olduser> ```

## Database Users

* user is the name of the user you want to own the database.
* dbname is the name of the database you want to create

``` createdb user dbname; ```

### Connect to database
``` \c dbname ```

### Change database owner
``` ALTER DATABASE name OWNER TO new_owner; ```



## Database

### Create new database

``` $ sudo -u dbownername createdb dbname ```

or in PGAdmin

* connect by double-clicking on server
* right click on Databases and add new


## Resources
[How To Install and Use PostgreSQL on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04#using-postgresql-roles-and-databases)

[How to manage PostgreSQL databases and users from the command line](https://www.a2hosting.com/kb/developer-corner/postgresql/managing-postgresql-databases-and-users-from-the-command-line#Adding-an-existing-user-to-a-database)