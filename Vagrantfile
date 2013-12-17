# -*- mode: ruby -*-
# vi: set ft=ruby :

####################################
# Vagrantfile for creating a new base box for use with Vagrant-DSpace
# 
#  
#
Vagrant::Config.run do |config|

    # Every Vagrant virtual environment requires a box to build off of.
    config.vm.box = "precise64"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"

    # Turn on SSH forwarding (so that 'vagrant ssh' has access to your local SSH keys, and you can use your local SSH keys to access GitHub, etc.)
    config.ssh.forward_agent = true

    config.vm.customize ["modifyvm", :id, "--nictype1", "virtio"]

end
