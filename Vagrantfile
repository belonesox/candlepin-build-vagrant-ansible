# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
#Vagrant.require_plugin("vagrant-hosts")
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "centos7min"
  #config.vm.box_url = "https://f0fff3908f081cb6461b407be80daf97f07ac418.googledrive.com/host/0BwtuV7VyVTSkUG1PM3pCeDJ4dVE/centos7.box"
  config.vm.synced_folder '.', '/vagrant', disabled: true
  
  config.vm.define "candlepin" do |conf|
    conf.vm.box = "centos7min"
    conf.vm.network "private_network", ip: "192.168.1.2"
    conf.vm.hostname = "subscription.virtuozzo.com"    
    conf.vm.network "forwarded_port", guest: 22,    host: 6022, id: 'ssh'    
    #conf.vm.network "forwarded_port", guest: 443,  host: 6443
    #conf.vm.network "forwarded_port", guest: 8443, host: 6444
    #conf.vm.network "forwarded_port", guest: 5432, host: 6432
    if Vagrant.has_plugin?("vagrant-hosts")
      conf.vm.provision :hosts, :sync_hosts => true    
    end  
    conf.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.groups = {
          "candlepin" => ["candlepin"],
      }        
      ansible.playbook = "candlepin.yml"
    end  
  end

  config.vm.provider "virtualbox" do |conf|
    # Display the VirtualBox GUI when booting the machine
    conf.gui = false
    conf.memory = "512"
    conf.cpus = 2
  end

end
