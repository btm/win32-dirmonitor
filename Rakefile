require 'rake'
require 'rake/clean'
require 'rake/testtask'

CLEAN.include("**/*.gem", "**/*.rbc", "**/*.rbx")

namespace :gem do
  desc "Create the win32-dirmonitor gem"
  task :create do
    spec = eval(IO.read('win32-dirmonitor.gemspec'))
    if Gem::VERSION < "2.0"
      Gem::Builder.new(spec).build
    else
      require 'rubygems/package'
      Gem::Package.build(spec)
    end
  end
end

desc 'Run the example program'
task :example do |t|
  ruby '-Ilib examples/example_dirmonitor.rb'
end

Rake::TestTask.new(:test) do |t|
  t.warning = true
  t.verbose = true
end

task :default => :test