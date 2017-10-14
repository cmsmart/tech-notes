# Front_End

## Example of 'if' statement in layout

```        
    <% if current_page?(root_path) %>
        <h1>My Title</h1>
    <% else %>
        <h1><a href="/">My Title</a></h1>
    <% end %>
```


## Set dynamic attributes in layout template based on page values 

e.g.

in appllication.html.erb


call @page_title variable from views or use default if not set

```<title>Site Title | <%= @page_title || "Admin area"%></title>```

in examplepage.html.erb

at top of page set value of variable (for example, this the title of the content on thsi page)

```<% @page_title = @book.title %>```


## Create new layouts and use on different pages

e.g.

#### Create new layout
Create a new file under views/layouts by copying  application.html.erb and call it admin.html.erb

#### Add to controller

``` 
class ExampleController < ApplicatioController

    layout 'admin'

```
