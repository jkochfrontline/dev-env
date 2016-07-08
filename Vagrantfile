###########################################
#                                         #
#     A Development Box to Build RPM's    #
#                                         #
###########################################
#
#

## Vagrant Quick Cluster

nodes = [
  # dev box
  { :hostname => 'builder', :cpus => 2, :mem => 1024, :ip => '172.168.0.108', 
    :url => 'https://github.com/holms/vagrant-centos7-box/releases/download/7.1.1503.001/CentOS-7.1.1503-x86_64-netboot.box'
  }
]

## --- Constants ---- ##
HOME = File.dirname(__FILE__)

## --- Scripts ---- ##

# install base packages required for dev
$install_dependencies = <<SCRIPT
  sudo yum -y install epel-release
  sudo yum -y install nginx
  sudo systemctl start nginx
SCRIPT

## --- Vagrant Configuration ---- ##
Vagrant.configure("2") do |config|

  nodes.each do |node|

    # Set resources
    config.vm.provider "virtualbox" do |vb|
      vb.customize ['modifyvm', :id, '--memory', node[:mem]]
      vb.customize ['modifyvm', :id, '--cpus', node[:cpus]]

      # do not change
      vb.customize ['modifyvm', :id, '--hwvirtex', 'on']
    end

    # Define Box
    config.vm.define node[:hostname] do |instance|
      instance.vm.box = node[:hostname]
      instance.vm.box_url = node[:url]
      instance.vm.host_name = node[:hostname]# + '.' + domain
      instance.vm.network 'private_network', ip: node[:ip]
      instance.vm.synced_folder "share/", "/home/vagrant/"
    end # end define

    # Cache
    config.cache.auto_detect = true

    # Scripts
    config.vm.provision "shell", inline: $install_dependencies

  end # end nodes
  
end