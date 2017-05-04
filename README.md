## :muscle: KMS is (K)Candidate Master of Sports :muscle:

[![Join the chat at https://gitter.im/kms-app/Lobby](https://badges.gitter.im/kms-app/Lobby.svg)](https://gitter.im/kms-app/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![Gem Version](https://badge.fury.io/rb/kms.svg)](https://badge.fury.io/rb/kms) [![Build Status](https://travis-ci.org/webgradus/kms.svg?branch=master)](https://travis-ci.org/webgradus/kms)

[![Dependency Status](https://gemnasium.com/badges/github.com/webgradus/kms.svg)](https://gemnasium.com/github.com/webgradus/kms)

KMS is a modern and flexible Ruby on Rails content management system with modular approach. It utilizes the most latest features from Rails and PostgreSQL (such as json column type, for example). Mostly inspired by LocomotiveCMS, but in contrast with it KMS relies on robust PostgreSQL database and doesn't provide all-in-one solution. The basic idea behind KMS: minimal core, extendable via extensions (engines). So you can take only what you need.

We, at [@webgradus](http://webgradus.com), used this CMS for our clients needs over past 1 year and now it's ready to be open sourced.
So feel free to use it in your projects.

## Built with good tools
* Ruby on Rails (>= 4.2, Rails 5 supported as well)
* Angular.js
* Responsive Dashboard template
* Liquor template language
* PostgreSQL (recommended for DB)

## Features included:
- [x] Minimal **basis/core** - Templates, Pages, Assets and Snippets
- [x] Extendable via Rails Engines
- [x] Beautiful and responsive admin panel
- [x] Simple and Powerful Template language - [Liquor](https://github.com/evilmartians/liquor)
- [x] Built-in documentation/help

![Screenshot](http://webgradus.com/images/KMS.jpg)

## Installation

1. Add to Gemfile

        gem "kms"
        # or for edge version:
        gem "kms", github: "webgradus/kms"

2. Setup database.yml (only PostgreSQL 9.2+ supported)

3. Run generator:

        rails g kms:install

4. Copy migrations:

        rails kms:install:migrations

5. Migrate:

        rails db:migrate

6. Set locale in your main app.

7. Precompile assets (if it will be production app):

        RAILS_ENV=production bundle exec rails assets:precompile

8. Run it using your favorite webserver - unicorn, puma, thin
9. Open your browser at **http://localhost:3000/kms** and sign up first admin user.

## Getting started
Please watch this video to start working in KMS:

[![Getting started in KMS - Ruby on Rails CMS](http://img.youtube.com/vi/WPZoWyd-thE/0.jpg)](https://youtu.be/WPZoWyd-thE "Getting started in KMS - Ruby on Rails CMS")

## Amazon S3 for assets storage

By default, KMS offers local file system as storage for your assets. But you could use Amazon S3 as well. Just follow these simple steps:

1. Add to Gemfile special gem for storing secrets. For example, this could be `dotenv-rails` or `figaro`. Don't forget to `bundle install`

        gem 'dotenv-rails'

2. Setup your `.env` file with these variables:

        KMS_ASSETS_STORAGE=fog
        AWS_ACCESS_KEY_ID=your_access_key
        AWS_SECRET_ACCESS_KEY=your_secret_key
        AWS_BUCKET=bucket_name
        AWS_REGION=eu-central-1 # or region you want

3. If you ran `rails g kms:install`, then you should have config/initializers/carrierwave.rb. Feel free to customize it.

        CarrierWave.configure do |config|
          if ENV['KMS_ASSETS_STORAGE'] == 'fog'
            config.fog_provider = 'fog/aws'
            ...

## Extensions
* [kms_models](https://github.com/webgradus/kms_models)
* [kms_feedback](https://github.com/webgradus/kms_feedback)
* [kms_catalog](https://github.com/webgradus/kms_catalog)
* [kms_shop](https://github.com/webgradus/kms_shop)
* [kms_seo](https://github.com/webgradus/kms_seo)

## Contributing

Please follow [CONTRIBUTING.md](CONTRIBUTING.md).

## Running problems

* Make sure you have "pids" and "sockets" folders in project's "tmp" folder (if using Puma especially)
