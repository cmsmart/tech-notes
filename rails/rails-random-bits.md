### E.G of using `rails console` to create dummy users and profiles in model:

``` user = User.create!(email: 'one@example.com', password: 'password') ```

``` Profile.create!(user: user, username: 'one', name: 'One McOneFace')```

*Note - create! enforces validation (i.e. with the !)


## add column to table

```rails g migration add_newcolumnname_to_tablenames nameofnewcolumn```

``` rails db:migrate```

## join table

``` rails g migration create_join_table :products, :categories, table_name: :categorization ```
or

```rails g migration CreateJoinTableCategoryProduct category product```

## update attributes

```variable = Class.find(x)```

```variable.update_attribute(:name, "value")```



## MailGun

add     

``` gem 'mailgun-ruby', '~>1.1.6'```

see gem docs.
add to config/development.rb and change info on environment variables (note the .fetch method from ruby docs which ensures the key is present)

```
  config.action_mailer.delivery_method = :mailgun
  config.action_mailer.mailgun_settings = {
    api_key: ENV.fetch('MAILGUN_API_KEY'),
    domain: ENV.fetch('MAILGUN_DOMAIN'),
  }
```

add dotenv gem and set environment variables in .env file in root. also add .env to .gitignore.

other config actions ...


## Creating foreign keys

an example of looking for the reference in a table that has a different name to the attribute

```
t.references :listing, foreign_key: true
t.references :guest, foreign_key: { to_table: :users }
```