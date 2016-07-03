# Vagrant (Part 1)

## Why Vagrant?

Vagrant is an open source software that automates processes, for example it installs software packages (dependent on your config files) while booting the project. Using vagrant for your projects offers you the benefit to set up multiple virtual machines (VM) with different environments that can be isolated from each other to avoid conflicts between operating systems (e.g. Mac, Linux, Ubuntu, Fedora, etc.) and software packages. The other benefit is that you can destroy one VM to startup an exact copy of the destroyed VM in minutes (based on the performance of your network connection and computer) in case you have screwed up your project and have syncing folders enabled.

## Setup Vagrant

First, you need to download the vagrant package for your computer operating system from this website:
[Vagrantup.com](https://www.vagrantup.com/downloads.html). Then follow the instructions and install the software. After the successful installation it will add vagrant automatically to your system path, so that it is available from your command line interface (CLI).

You also need to install a virtual machine (engine) as a provider, e.g. virtual box or VM Fusion software in order to use vagrant. Get virtualbox for free from this page:
[Virtualbox.org](https://www.virtualbox.org/wiki/Downloads)

Then go to this page to find the vagrant boxes (ready to go packages) suitable to your needs:
[Atlas/Hashicorp](https://atlas.hashicorp.com/boxes/search)

#### After that create your first vagrant project:
```
$ mkdir my_vagrant_project
$ cd my_vagrant_project
$ vagrant init
```

It will then create a `Vagrantfile` in your new vagrant project directory.

Now, let's say you have chosen the vagrant box `ubuntu/trusty64` for `Ubuntu 14.04 LTS` from the atlas.hashicorp.com website. 

#### Then add the vagrant box to your vagrant directory with:

```
$ vagrant box add ubuntu/trusty64
```

#### Open the Vagrantfile with:
```
$ vim Vagrantfile
```
or:
```
$ nano Vagrantfile
```

#### Now in the `Vagrantfile` you need to find the lines:

a) Box

```
config.vm.box = "base"
```
#### and change it to:
```
  config.vm.box = "ubuntu/trusty64"
```

b) Provider

```bash
# config.vm.provider "virtualbox" do |vb|
#   # Display the VirtualBox GUI when booting the machine
#   vb.gui = true
#
#   # Customize the amount of memory on the VM:
#   vb.memory = "1024"
# end
```
#### and change it for example to:

 ```bash
 config.vm.provider "virtualbox" do |vb|
  vb.memory = "2048"
  vb.cpus = "2"
 end
```

#### To start the machine, finally run:
```bash
$  vagrant up
```

#### You can run following to use the default ssh provided by vagrant:
```bash
vagrant ssh
```

#### Notes: 

- In case it is required, the basic `username` = `vagrant` and `password` = `vagrant`.
- Basically your vagrant is now ready for `$ vagrant up` but at the current state it doesn't do a lot except starting and stopping the virtual machine. This is why we need to do some further configurations to match a project's needs. 
- Before you edit your `Vagrantfile` learn how to use a text editor from the command line like [vim](http://www.openvim.com), nano, etc.

In the next chapter we will learn how to add more configs to the `Vagrantfile`.
