# Ruby on Rails

## Server
To run a local server 

 ``` rails s ```
 * Note - if you change something in initializers directory you need to restart.

## Routes

Show all routes

``` ruby routes ```

 Set the default index page in config/routes.rb

 e.g. ``` root 'home#index' ```

## Gems

Adding new gems
* Manually add to the gemfile
* Run ``` bundle install ```


 ## Variables
* to use a variable from home controller need to make the html files erb
* need to put variable in ruby tags

```<% no equals sign don't see the output %>```

``` <%= shows the output %> ```


## Tables / Database

* Look at schema.rb to see what tables have been created

### Index
A database index is a data structure that improves the speed of operations in a table. Indexes can be created using one or more columns, providing the basis for both rapid random lookups and efficient ordering of access to records.

eg add_index :page, :some_id

### Log in to rails database

``` rails db ```


## Postgres

``` rails new myapp --database=postgresql```

### Check what database is being used in rails console

``` ActiveRecord::Base.connection.current_database ```

### Add  database user details to config/database.yml (if user has a password)

  host: localhost
  username: pguser
  password: pguser_password


### Create your databases
```rake db:create```

### To restart postgresql

``` sudo /etc/init.d/postgresql restart ```