# Rails

### [RBEnv](https://github.com/sstephenson/rbenv/)

List current ruby version: `rbenv versions`

Set local/directory version of ruby:`rbenv local <VERSION>`

After installing a gem that adds new binaries (new commands):`rbenv rehash`

### [Ruby Gems](http://docs.rubygems.org/)

Updating gem system:`gem update --system --no-document`

### [Bundler](http://gembundler.com/)

Install gems from current bundle:`bundle install` **or:** `bundle install --without production`

Run an executable that comes with a gem in your bundle:`bundle exec <GEM COMMAND>`

Update one gem: `bundle update --conservative <GEM NAME>`

### [Rails](http://guides.rubyonrails.org/)

Create a new Rails project:`rails new <APP NAME>`

Create Rails database:`rake db:create`

Update Rails database:`rake db:migrate`**or:**`rake db:migrate RAILS_ENV=production`

Run Rails server:`rails server`

Rails console:`rails console --sandbox`

Rails console bypass model validation:`XXXXXX.update(admin: true) XXXXXX.save(:validate => false)`

### Capistrano

Deploy:`bundle exec cap TASKHERE deploy`

### Heroku

Create app:`heroku create`

Push app:`git push heroku master`

Auth Heroku: `heroku auth:login`

Open app:`heroku open`

Run console:`heroku run rails console`

Migrate database:`heroku run rake db:migrate`

If you want to run sqlite locally and pg on heroku, your gemfile needs to look like this:

```
group :development do
   gem 'sqlite3'
end

group :production do
   gem 'pg'
end
```

You may need to add the Ruby version to your gemfile as well:`ruby '1.9.3'`

To get your assets to properly compile on heroku, change your production.rb file to say true here instead of false:`config.assets.compile = true`

[Deploy to heroku through git](https://devcenter.heroku.com/articles/git).

Deploy with branch name other than master or main: `git push heroku my-branch:main`

### Dokku

Push app:`git push dokku master`

In your production group, you'll likely want these two gems:

```
gem 'pg' # postgres
gem 'rails_12factor' # for logging
```

SSH into server to run dokku commands. Use `dokku --help` for list of commands.

[Use git to deploy Heroku app](https://devcenter.heroku.com/articles/git).
