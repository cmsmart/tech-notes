# MySQL

## Database dump

``` mysqldump -u username -p database > database.sql ```

## Database push

``` mysql -u root -p database < database.sql ```


### Show databases

``` mysqlshow -p ```

### Create a database

``` mysqladmin -u user -p create databasename ```

### Delete a database

``` mysqladmin -u root -p drop databasename ```

### Log in to MySQL

``` mysql -u DBuser -h DBservername(eg localhost) -p ```

### Get a list of MySQL users and hosts

```mysql > select user,host from mysql.user; ```

### Find user privileges

``` mysql > show grants for 'user'@'host'; ```

### Create a user

``` mysql > grant all on *.* to 'user'@'host' identified by 'password'; ```

### Revoke user privileges

``` mysql > revoke all on *.* from 'user'@'host'; ```

### Show tables in a db

``` use databasename; ```

``` show tables; ```