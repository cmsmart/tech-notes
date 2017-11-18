# Images

* stored under app/assets/images

### to use in views

``` <%= image_tag('example.png') %>```

#### you can add attributes

``` <%= image_tag('example.png'), size: '90x95', alt: 'logo') %>```
``` <%= image_tag @example_url, alt: @example.attribute %>```


### to use in scss/css

 ``` background: image-url("example.jpg"); ```