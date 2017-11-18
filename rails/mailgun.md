# MailGun

## Suport email example

### add mailgun gem

```gem 'mailgun-ruby', '~>1.1.6'```

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

### create mailer model

in app/mailers/supoprt_mailer.rb

```
class SupportMailer < ApplicationMailer
  def contact_support(from_email, message)
    @from_email = from_email
    @message = message
    support_email = ENV.fetch('SUPPORT_EMAIL')
    mail(to: support_email, subject: "Support request from #{@from_email}")
  end
end
```

#### set email support email value in .env

``` SUPPORT_EMAIL = example@example.com ```

#### set up support controller

support_controller.rb

```
class SupportController < ApplicationController
  def new
    @error_messages = []
  end

  def create
    from_email = params[:email]
    message = params[:message]

    @error_messages = []
    @error_messages << 'Please enter your email' if from_email.blank?
    @error_messages << 'Please enter your message' if message.blank?

    # No errors, all good
    if @error_messages.empty?
      # Send the message to our support email address
      SupportMailer.contact_support(from_email, message).deliver_now
      # Show success message
      render :success
    # There are errors
    else
      # Show the user the errors
      render :new
    end
  end
end
```

#### set up views

support_mailer/contact_support.html.erb

```
<h1>Support message</h1>

---

<p>From: <%= @from_email %></p>

<p>Message:</p>
<%= simple_format @message %>
```

support_mailer/contact_support.text.erb

```
Support message

---

From: <%= @from_email %>

Message:
<%= @message %>
```

support/new.html.erb

``` 
<h1>Support</h1>

<p>Please message our support team here:</p>

<%= form_with(url: support_url, local: true) do |f| %>
  <% unless @error_messages.empty? %>
    <% @error_messages.each do |message| %>
      <p><%= message %></p>
    <% end %>
  <% end %>

  <div>
    <%= f.label :email %>
    <%= f.email_field :email %>
  </div>

  <div>
    <%= f.label :message %>
    <%= f.text_area :message, rows: 6 %>
  </div>

  <%= f.button 'Send' %>
<% end %>

``` 
support/success.html.erb
```
<h1>Support</h1>

<p>Your message has been successfully received.</p>

```

#### Create routes

```  get '/support' => 'support#new'```

``` post '/support' => 'support#create'```
