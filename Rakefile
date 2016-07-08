# #######################
#                       #
# Windows Dev Env Setup #
# `rake` for usage      #
#                       #
#########################
 
## require
require 'rake/clean'
require 'net/http'

import 'share/lib/common.rb'

## consts
HOME = File.dirname(__FILE__)


#TODO, specifiy version
#vbguest - 0.9.0
BASE_VAGRANT_PLUGINS = [
  "vagrant-vbguest",
  "vagrant-butcher",
  "vagrant-vbox-snapshot",
  "vagrant-share",
  "vagrant-cachier"
]


## Tasks
task :default do
  Rake::Task["help:examples"].invoke
end

# Install workstation deps
namespace :install do
  
  def installVagrantPlugin(pluginName)
    system "vagrant --version"

#vagrant plugin uninstall #{pluginName} && 
    shell_prompt(
      "./",
      "vagrant plugin install #{pluginName}",
      "install vagrant plugin #{pluginName}"
    )
  end

  desc "Installs required vagrant plugins for development"
  task :vagrantPlugins do
    BASE_VAGRANT_PLUGINS.each{ |plugin| installVagrantPlugin(plugin) }
  end

  desc "Full environment setup."
  task :all do

    # Install dependencies
    Rake::Task["install:vagrantPlugins"].invoke
    
    puts "\nEnvironment setup complete!"
  end
end


namespace :help do
  desc "usage examples"
  task :examples do
    puts "\n\n"
    puts "---------------------------"
    puts " Usage Examples:"
    puts "  `rake -T` lists all the available tasks"
    puts "  `rake clean` cleans up misc files"
    puts "  `rake install:all` will automatically install and configure your environment"
    puts "---------------------------"
    puts "\n\n"
  end

  task :default => :examples
end