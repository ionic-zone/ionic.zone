source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', 163 #versions['github-pages']
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
gem 'wdm', '>= 0.1.0' if Gem.win_platform?
