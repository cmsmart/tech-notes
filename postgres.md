# Postgres

## Users

Switch to postgres account

``` sudo -i -u postgres ```

Access postgres prompt

``` psql ```

Exit 

``` \q ```


### Create new role

When logged in as postgres account create new user

``` postgres@server:~$ createuser --interactive ```



### Add an existing user to a database

``` GRANT permissions ON DATABASE dbname TO username; ```

for example

``` GRANT ALL PRIVILEGES ON DATABASE dbname TO username; ```


## Database

* user is the name of the user you want to own the database.
* dbname is the name of the database you want to create

``` createdb user dbname ```