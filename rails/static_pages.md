# Static Pages

You can create static pages by creating a controller 

e.g.

``` rails g controller StaticPages home about ``` 

and set the routes in routes.rb

e.g.

```  root 'static_pages#home' ```

``` get '/about', to: 'static_pages#about' ```