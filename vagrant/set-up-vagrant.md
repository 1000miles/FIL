# Setup Vagrant

First, you need to download the vagrant package for your computer operating system from this website:
[Vagrantup.com](https://www.vagrantup.com/downloads.html)

Then follow the instructions and install the software. After the successful installation it will add vagrant automatically to your system path, so that it is available from your command line interface (CLI).

You also need to install a virtual machine as a provider, e.g. virtual box or VM Fusion software in order to use vagrant. Get virtualbox for free from this page:
[Virtualbox.org](https://www.virtualbox.org/wiki/Downloads)


Then go to this page to find the vagrant boxes suitable to your needs:
[Atlas/Hashicorp](https://atlas.hashicorp.com/boxes/search)

After that create your first vagrant project:
```
$ mkdir my_vagrant_project
$ cd my_vagrant_project
$ vagrant init
```
It will then create a `Vagrantfile` in your new vagrant project directory.

Let's say you have chosen the vagrant box `hashicorp/precise64` for `Ubuntu 12.04 LTS` from the atlas.hashicorp.com website. Now add the vagrant box to your vagrant directory with:

```
$ vagrant box add hashicorp/precise64
```

Now in the `Vagrantfile` you need to find the lines

a) Box

```
config.vm.box = "base"
```
and change it to:
```
  config.vm.box = "hashicorp/precise64"
```

b) Provider

```
# config.vm.provider "virtualbox" do |vb|
#   # Display the VirtualBox GUI when booting the machine
#   vb.gui = true
#
#   # Customize the amount of memory on the VM:
#   vb.memory = "1024"
# end
```
 and change it for example to:

 ```
 config.vm.provider "virtualbox" do |vb|
  vb.memory = "2048"
  vb.cpus = "2"
 end
```

To start the machine, finally run:
```
$  vagrant up
```

You can run following to use the default ssh provided by vagrant:
```
vagrant ssh
```

That's it. In the next session I will show you how to setup a file that automatically installs or updates software packages you might need for your projects. :)
