# Image uploading with Shrine

## Creating image fields

image field should be of type text and have suffix _data

 eg

 ``` t.text :profile_photo_data```

## Add gems
 
  ### Shrine
  ```gem "shrine"```
  ### AWS for storing images
  ```gem 'aws-sdk', '~> 3'```

  ### Shrine Dependencies
  ```gem 'fastimage'```

  ```gem 'image_processing'```

  ```gem 'mini_magick'```         



## Set up a file system for storage and set variables in .env file

### Set up config/initializers/shrine.rb and add options for AWS3: 

```
require "shrine"
require "shrine/storage/s3"

s3_options = {
  access_key_id:     ENV.fetch("S3_ACCESS_KEY_ID"),
  secret_access_key: ENV.fetch("S3_SECRET_ACCESS_KEY"),
  region:            ENV.fetch("S3_REGION"),
  bucket:            ENV.fetch("S3_BUCKET"),
}

Shrine.storages = {
  cache: Shrine::Storage::S3.new(prefix: "cache", **s3_options),
  store: Shrine::Storage::S3.new(prefix: "store", **s3_options),
}
```

### IMPORTANT 
* Add keys to .env file and add .env to .gitignore

* Also can add public/uploads to .gitignore

### Create a new file in your model folder. 
* call it image_uploader.rb
* Set validation and optional image size alternatives

and add 
```
class ImageUploader < Shrine
    include ImageProcessing::MiniMagick
  
    plugin :activerecord
    plugin :determine_mime_type
    plugin :logging, logger: Rails.logger
    plugin :remove_attachment
    plugin :store_dimensions
    plugin :validation_helpers
    plugin :versions, names: [:original, :thumb]
  
    Attacher.validate do
      validate_max_size 2.megabytes, message: 'is too large (max is 2 MB)'
      validate_mime_type_inclusion ['image/jpg', 'image/jpeg', 'image/png', 'image/gif']
    end
  
    def process(io, context)
      case context[:phase]
      when :store
        thumb = resize_to_limit!(io.download, 200, 200)
        { original: io, large: size_700, medium: size_500, thumb: thumb }
      end
    end
  end
  ```

  ## Include class inside relevant model

  e.g.

  ```
  class Profile < ApplicationRecord
    include ImageUploader[:image_name]
  end
```

  ## Add fields to relevant form

  e.g.

```
<div class="field">
    <%= form.label : image %>
    <%= form.file_field :image, id: :profile_image %>
</div>

<div class="field">
    Remove attachment: <%= form.check_box :remove_image %>
</div>
```

## Add to controller params (remove)

e.g.

```
  def profile_params
      params.require(:profile).permit(:name, :description, :profile_image, :remove_image)
end
```

## Style fields to use image 
```

  <% if @profile.image.present? %>
    <figure>
    <%= image_tag @profile.image_url(:thumb), alt: " #{@profile.name}" %>
    </figure>
  <% else %>
    <p>No image</p>
  <% end %>

  ```


  ## Resources

  [Uploading Files With Rails and Shrine](https://code.tutsplus.com/tutorials/uploading-files-with-rails-and-shrine--cms-27596)

  [Rails File Uploading You Can Believe in with Shrine](https://www.sitepoint.com/rails-file-uploading-you-can-believe-in-with-shrine/)