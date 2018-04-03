# MySQL

## Database dump

``` mysqldump -u username -p database > database.sql ```

## Database push

``` mysql -u root -p database < database.sql ```


### Show databases

``` mysqlshow -u user -p ```

### Create a database

``` mysqladmin -u user -p create databasename ```

### Delete a database

``` mysqladmin -u user -p drop databasename ```

### Log in to MySQL

``` mysql -u user -p ```

``` mysql -u user -h DBservername(eg localhost) -p ```

### Get a list of MySQL users and hosts

```mysql > SELECT user,host FROM mysql.user; ```

### Find user privileges

``` mysql > SHOW GRANTS FOR 'user'@'host'; ```

### Create a user

``` CREATE USER 'user'@'localhost' IDENTIFIED BY 'password'; ```

### Grant privileges

``` mysql > GRANT ALL ON *.* TO 'user'@'host' IDENTIFIED BY 'password'; ```

``` GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost'; ```

### Revoke user privileges

``` mysql > REVOKE ALL ON *.* FROM 'user'@'host'; ```

### Show tables in a db

``` USE databasename; ```

``` SHOW TABLES; ```