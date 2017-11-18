#Heroku with Rails 5.x

``` heroku login```

* git commit

``` heroku create ```

* check if remote was added by running

``` git config --list | grep heroku ```

* push to Heroku

``` git push heroku master ```

* If no error migrate database

``` heroku run rake db:migrate ```


* To go to app in browser

``` heroku open ```

* seedng 

```heroku run rake db:seed```

### Destroy it

``` heroku apps:destroy --app example```

### Drop heroku database

``` heroku pg:reset DATABASE ```


## Resources

[Getting Started with Rails 5.x on Heroku](https://devcenter.heroku.com/articles/getting-started-with-rails5)