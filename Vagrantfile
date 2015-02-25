# -*- mode: ruby -*-
# vi: set ft=ruby :

####################################
# Vagrantfile for creating a new base box for use with Vagrant-DSpace
# 
#  
#
#Vagrant::Config.run do |config|
Vagrant.configure("2") do |config|

    # Every Vagrant virtual environment requires a box to build off of.
    config.vm.box = "trusty64"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

    # Turn on SSH forwarding (so that 'vagrant ssh' has access to your local SSH keys, and you can use your local SSH keys to access GitHub, etc.)
    config.ssh.forward_agent = true

    # name this machine
    config.vm.define :dspace do |t|
    end

    # simple shell provisioning block for specifying the packages we'd like to be installed in this base machine
    config.vm.provision "shell", inline: "echo provisioning base package set to make this machine useable with Vagrant-DSpace..."

    # install Ruby 1.9, apt-spy2, curl, geoip-bin, all required to make
    # initial provisioning more resilient no matter where you might be
    # (Ubuntu deb mirror configuration is notoriously fragile)
    config.vm.provision "shell", inline: "apt-get -y install ruby1.9.3"
    config.vm.provision "shell", inline: "apt-get -y install curl"
    config.vm.provision "shell", inline: "apt-get -y install geoip-bin"
    config.vm.provision "shell", inline: "apt-get -y install zlib1g-dev"
    config.vm.provision "shell", inline: "gem install apt-spy2"

end
