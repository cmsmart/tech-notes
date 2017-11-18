# Static Pages

You can create static pages by creating a controller 

e.g.

``` rails g controller Static home about ``` 

and set the routes in routes.rb

e.g.

```  root 'static#home' ```

``` get '/about', to: 'static#about' ```