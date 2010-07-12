
require 'rake/tasklib'

require "rubygems"
require "bundler"
Bundler.setup(:default, :test, :build)

require 'lib/ruote-kit/version'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gemspec|
    gemspec.name = 'ruote-kit'
    gemspec.version = RuoteKit::VERSION
    gemspec.summary = 'ruote workflow engine, wrapped in a loving rack embrace'
    gemspec.description = 'ruote-kit is a RESTful Rack app for the ruote workflow engine'
    gemspec.email = 'kenneth.kalmer@gmail.com'
    gemspec.homepage = 'http://github.com/kennethkalmer/ruote-kit'
    gemspec.authors = ['kenneth.kalmer@gmail.com', 'John Mettraux']
    gemspec.extra_rdoc_files.include '*.txt'

    gemspec.files.include 'lib/ruote-kit/public/**/*'
    gemspec.executables.clear

    gemspec.add_dependency 'bundler', '>=0.9.5'
    gemspec.add_dependency 'sinatra', '>=0.9.4'
    gemspec.add_dependency 'sinatra-respond_to', '>=0.4.0'
    gemspec.add_dependency 'haml', '>= 2.2.5'
    gemspec.add_dependency 'rufus-json', '>= 0.2.3'
    gemspec.add_dependency 'ruote', '>= 2.1.10'
    gemspec.add_development_dependency 'rake'
    gemspec.add_development_dependency 'rspec'
    gemspec.add_development_dependency 'jeweler'
    gemspec.add_development_dependency 'webrat'
    gemspec.add_development_dependency 'test-unit', '~> 1.2.3'
    gemspec.add_development_dependency 'rack-test'
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler not available. Install it with 'gem install jeweler'"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :spec #=> :check_dependencies

task :default => :spec

begin
  require 'yard'
  YARD::Rake::YardocTask.new
rescue LoadError
  task :yardoc do
    abort "YARD is not available. In order to run yardoc, you must: sudo gem install yard"
  end
end
