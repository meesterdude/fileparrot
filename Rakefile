# encoding: utf-8

require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'



require 'jeweler'
Jeweler::Tasks.new do |gem|
  gem.version = File.read('VERSION').chomp
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "fileparrot"
  gem.homepage = "http://github.com/meesterdude/fileparrot"
  gem.license = "MIT"
  gem.executables   = ["fileparrot"]
  gem.summary = %Q{makes custom data capture to text files easy}
  gem.description = %Q{fileparrot is a simple tool to help you capture data to textfiles. use it for journals, workout logs, or whatever you desire.}
  gem.email = "violentpurr@gmail.com"
  gem.authors = ["Russell Jennings"]
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end


task :default => :test

require 'rdoc/task'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "fileparrot #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
