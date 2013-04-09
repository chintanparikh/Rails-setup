#!/usr/bin/env ruby

appname = ARGV[0]
path = `pwd`.strip
path_to_app = path. + '/' + appname

gemfile = "source 'https://rubygems.org'

# system
gem 'rails'
gem 'sqlite3'

# to get rails console working
gem 'rb-readline'

group :assets do
  gem 'sass'
  gem 'sass-rails' 
  gem 'coffee-rails'
  gem 'therubyracer', :platform => :ruby
  gem 'formtastic'
  gem 'uglifier'
end

group :development, :test do
  gem 'debugger'
  gem 'rspec-rails'
  gem 'factory_girl'
  gem 'factory_girl_rails'
  gem 'ffaker'
  gem 'haml-rails'
end

group :test do
  gem 'rspec'
  gem 'shoulda-matchers'
  gem 'database_cleaner'
end

gem 'awesome_print'"

# create and cd into new rails app
Dir.chdir path
system("rails new #{appname} -T")
Dir.chdir path_to_app

# change Gemfile
File.open("#{path_to_app}/Gemfile", 'w') { |file| file.write(gemfile) }

# re-run bundle install to updated Gems
system("bundle update")
system("bundle install")

# setup rspec
system("rails generate rspec:install")

# setup formtastic
system("rails generate formtastic:install")

# delete the files we don't need
system("rm -rf 'public/index.html'")

