# Stripe payments

```gem 'stripe'```

### Add file to initializers/stripe.rb

```
Rails.configuration.stripe = {
  :publishable_key => ENV['STRIPE_PUBLISHABLE_KEY'],
  :secret_key      => ENV['STRIPE_SECRET_KEY']
}

Stripe.api_key = Rails.configuration.stripe[:stripe_secret_key]
``` 

### add keys to .env file
