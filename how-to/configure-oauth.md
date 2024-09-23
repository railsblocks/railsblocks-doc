# Configure OAuth

## Overview

OAuth make one-click login possible and easy.

OAuth is an open standard for authentication and authorization. 

RailsBlock has native support to Google and GitHub.

## Configure OAuth

### Google

Go to `https://console.cloud.google.com/apis/credentials` and create a new OAuth client ID.

### GitHub

Go to `https://github.com/settings/applications/new` and create a new OAuth application.

After creating the application, you will get a `Client ID` and `Client Secret`. 

Now edit the `config/initializers/omniauth.rb` file, set the `client_id` and `client_secret` for the `Google` and `GitHub` providers.

A sample configuration looks like this:

```ruby
Rails.application.config.middleware.use OmniAuth::Builder do
  github_oauth_key = Rails.application.credentials.github_oauth_key
  github_oauth_secret = Rails.application.credentials.github_oauth_secret
  provider :github, github_oauth_key, github_oauth_secret, scope: "read:user, user:email"

  google_oauth_key = Rails.application.credentials.google_oauth_key
  google_oauth_secret = Rails.application.credentials.google_oauth_secret
  provider :google_oauth2, google_oauth_key, google_oauth_secret
end

OmniAuth.config.allowed_request_methods = [:post]
```

