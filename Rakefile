require 'rubygems'
require 'rubygems/specification'
require 'rake'
require 'rake/gempackagetask'
require 'spec/rake/spectask'
 
GEM = "error-reporter"
GEM_VERSION = "0.0.1"
SUMMARY = "A Ruby error reporter for our errors service"
AUTHOR = "Simon Menke"
EMAIL = "simon@mrhenry.be"
HOMEPAGE = "http://github.com/mrhenry"

 
spec = Gem::Specification.new do |s|
  s.name = GEM
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.summary = SUMMARY
  s.require_paths = ['lib']
  s.files = FileList[
    'lib/**/*.rb',
    'rails/**/*.rb',
    'examples/**/*.rb',
    '[a-zA-Z]*.textile'].to_a
  
  s.author = AUTHOR
  s.email = EMAIL
  s.homepage = HOMEPAGE

  s.rubyforge_project = GEM # GitHub bug, gem isn't being build when this miss
  
  s.add_dependency 'httparty', '>= 0.2.6'
end

Spec::Rake::SpecTask.new do |t|
  t.spec_files = FileList['spec/**/*_spec.rb']
  t.spec_opts = %w(-fs --color)
end
  
Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end
 
desc "Install the gem locally"
task :install => [:package] do
  sh %{sudo gem install pkg/#{GEM}-#{GEM_VERSION}}
end
 
desc "Create a gemspec file"
task :make_spec do
  File.open("#{GEM}.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end
