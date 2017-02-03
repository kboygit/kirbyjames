source 'https://rubygems.org'
ruby '2.3.1'
require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'kramdown'
gem 'rack-jekyll', git: 'https://github.com/adaoraul/rack-jekyll.git'
gem 'rake'
gem 'puma'
gem 'pygments.rb'

group :production do
  gem 'pg', '0.18.4'
  gem 'rails_12factor'
end

group :jekyll_plugins do
  gem "jekyll-paginate"
  gem 'jekyll'
  gem 'jekyll-sitemap'
  gem 'jekyll-feed'
end
