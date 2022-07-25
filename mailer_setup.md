# Email Sending Configuration

## Gmail example

In `config/environment/[env].rb`

    config.action_mailer.raise_delivery_errors = false
    config.action_mailer.delivery_method = :smtp
    config.action_mailer.perform_deliveries = true
    config.action_mailer.perform_caching = false

    config.action_mailer.smtp_settings = {
      :address              => "smtp.gmail.com",
      :port                 => 587,
      :user_name            => "xxxxxxx@gmail.com",
      :password             => "app password, not gmail password"
      :authentication       => "plain",
      :enable_starttls_auto => true
    }

## Postmark example

1. Register an [postmark](https://postmarkapp.com/) account.
2. Create a *Server* in Dashboard page.
3. Add the Postmark Rails Gem to your Gemfile

    gem "postmark-rails"

4. Save your Postmark Server API Token to config/credentials.yml.enc by running rails secret then rails credentials:edit and adding:

    postmark_api_token: "xxxxxxxx-c401-48b0-b13d-xxxxxx"

Then set Postmark as your preferred mail delivery method via config/application.rb:

    config.action_mailer.delivery_method = :postmark

    config.action_mailer.postmark_settings = {
        api_token: Rails.application.credentials.postmark_api_token
    }

5. Generate a mailer, views, and preview

    $ bin/rails generate mailer test hello

6. Set up your mailer:

    class TestMailer < ApplicationMailer
        default from: 'service@canslim.org'

        def hello
            mail(
            subject: 'Hello from Postmark',
            to: 'example@gmail.com',
            from: 'service@canslim.org',
            html_body: '<strong>Hello</strong> dear Postmark user.',
            track_opens: 'true',
            message_stream: 'outbound')
        end
    end

7. Send an email from the console by calling deliver_now. Alternatively, you can call deliver_later to send the email asynchronously.

    $ bin/rails console
    >> TestMailer.hello.deliver_now