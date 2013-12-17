<h1>Vagrantbox-Ubuntu</h1>
A basic Vagrantfile for use in customizing a generic Vagrant base box for use in 
DSpace development. This project mostly exists so that we can modify the 
/etc/apt/sources.list file to enable the mirror method of picking an appropriate 
deb mirror, because we DSpace developers are all over the world, and hard-coding 
this file for servers in the US is just plain rude. 

<h2>But, also, Guest Additions!</h2>
Yes, the Virtual Box Guest Additions version number increases with each new version
of Virtual Box. And, alas, most generic Vagrant base box images don't ever
seem able to keep up. Darn them. One easy, though somewhat time-consuming, way to
deal with this is to install the [VB Guest plugin](https://github.com/dotless-de/vagrant-vbguest) 

<h2>How to use this project</h2>

Credit where credit is due, the entire idea for this project came from [this article](http://www.pvcloudsystems.com/2012/10/vagrant-modify-existing-box/).

<code>
vagrant up
vagrant ssh
</code>

Now you're free to modify the base box to match your needs. We recommend that you replace
/etc/apt/sources.list by one of the [methods listed here](http://askubuntu.com/questions/319433/making-mirror-mirrors-ubuntu-com-highly-available)

When you're done modifying the sources.list, it's a good idea to go ahead and update the packages.

<code>
sudo apt-get update
sudo apt-get upgrade
exit
</code>

If you'd like to pre-install any packages for your base image, now is the time to do so.

When you're done, exit the vagrant ssh session, and run

<code>
vboxmanage list runningvms
</code>

And look for the name that Virtual Box has given this machine, it will likely be something like this: 

<code>vagrantbox-ubuntu_dspace_1387309768</code>

Now run

<code>
vagrant package --base vagrantbox-ubuntu_dspace_1387309768 --output precise64.box
</code>

Wait for that to complete, when you have a new precise64.box all packaged up, run this:

<code>
vagrant box add precise64 precise64.box
</code>

And now, you will have your own personally-tweaked base box to use with Vagrant-DSpace, or for any Vagrant-based project that refers to a base box named "precise64".

<h2>Requirements</h2>
[Vagrant](http://www.vagrantup.com/)
[Virtualbox](https://www.virtualbox.org/)

<h2>Optional, but highly recommended</h2>
[VB Guest plugin](https://github.com/dotless-de/vagrant-vbguest) 
<code>  vagrant plugin install vagrant-vbguest</code>

<h2>License</h2>
This work is licensed under the [DSpace BSD 3-Clause License](http://www.dspace.org/license/), which is just a standard [BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause).
