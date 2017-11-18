## Drop down select list - Form Collection

```<%= form.collection_select :color_id, Color.all, :id, :color_name %>```

* :color_id is the foreign key that resides in the current table
* :Color.all specifies which records to include in the drop down list
* :id is the primary key in the Colors table
* :color_name is the field from the Colors table to display in the drop down list

### With attributes

```<%= form.collection_select :color_id, Color.all, :id, :color_name, include_blank: true %>```

### With ordering

```<%= form.collection_select :color_id, Color.order(:color_name), :id, :color_name, include_blank: true %>```

### With class

```<%= form.collection_select :color_id, Color.order(:color_name), :id, :color_name, { include_blank: true }, { class: "class_name" } %>```


## Using select2 for autocomplete

### Gems

```gem "select2-rails"```

* Also make sure jquery-rails gem is installed

### Add to your application.js file

```//= require select2```

and

```//= require jquery```

if not alredy

### Add to your application.css file

``` *= require select2```

### Add to your appication.js (or other js file)

```
$(document).ready(function() {
    $('.classname').select2();
});

```

### Add to your select list appropriate class name 

eg

```<%= form.collection_select :color_id, Color.order(:color_name), :id, :color_name, { include_blank: true }, { class: "classname" } %>```


### Resources
[Select2](https://select2.org/)
