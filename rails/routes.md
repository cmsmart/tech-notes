#Routes

## Redirect routes and paths in your routes.rb

e.g.

```resources :newpath, controller: 'oldpath'```

## Static page routes

e.g.

```  root 'static_pages#home' ```

``` get '/about', to: 'static#about' ```