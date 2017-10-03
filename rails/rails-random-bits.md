### E.G of using `rails console` to create dummy users and profiles in model:

``` user = User.create!(email: 'one@example.com', password: 'password') ```

``` Profile.create!(user: user, username: 'one', name: 'One McOneFace')```

*Note - create! enforces validation (i.e. with the !)


## add column to table

```rails g migration add_newcolumnname_to_tablename nameofnewcolumn```

``` rails db:migrate```



## update attributes

```variable = Class.find(x)```

```variable.update_attribute(:name, "value")```