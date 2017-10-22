# Geocoder with static map 

Example called 'Events'

## Create model
Must have 
* An address field
* A latitude address field
* A longitude address field (e.g. t.decimal :longitude, precision: 10, scale: 6)

## Add gem

```gem geocoder```

## Add geocoder to model/event.rb

``` geocoded_by :address```

``` geocoded_by :address ```

* and to prevent queries if address is unchanged

``` after_validation :geocode, if: ->(obj){ obj.address.present? and obj.address_changed? }```

* Note that is if address is just a single field called address.
Otherwise you can write a method that joins the columns together and then pass that

e.g.
```
def full_address
    [country, city, street].compact.join(‘, ‘)
end

geocoded_by :full_address

```

* Also if you have latitude and longitude fields with different names you can override the corresponding settings 

e.g.

```geocoded_by :address, latitude: :lat, longitude: :lon```


## Set up API
* Note that Google Static Maps API must be enabled when creating your API key in Google Developer

```rails generate geocoder:config```

### In config/initializers.geocoder.rb

Uncomment 
```
:lookup => :google, # for street addresses
:ip_lookup => :freegeoip # for IP addresses
```
and add Google API key (using .env file)
```   api_key:  ENV.fetch("GOOGLE_API")  # API key for geocoding service ```

## Add tag to display static map on show view

```
<%= image_tag "http://maps.googleapis.com/maps/api/staticmap?center=#{@event.latitude},#{@event.longitude}&markers=#{@event.latitude},#{@event.longitude}&zoom=7&size=640x400&key=AIzaSyA4BHW3txEdqfxzdTlPwaHsYRSZbfeIcd8",class: 'img-fluid img-rounded', alt: "#{@event.name} on the map"%>
```


## Resources
[Geocoder: Display Maps and Find Places in Rails](https://www.sitepoint.com/geocoder-display-maps-and-find-places-in-rails/)