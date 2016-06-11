# Vagrant Cheat Sheet

This cheat sheet is incomplete, it will list only the basics.

## Index

- vagrant help
- vagrant init
- vagrant box
- vagrant plugin
- vagrant up
- vagrant reload
- vagrant ssh
- vagrant provision
- vagrant suspend
- vagrant halt
- vagrant destroy
- vagrant status
- vagrant global-status
- vagrant push
- vagrant share


## Before you start

**Check if and which vagrant version is installed**
```bash
$ vagrant -v # short version
```
```bash
$ vagrant version # long version
```

**Get help**
```bash
$ vagrant -h
```

## Getting Started

**Initialize vagrant in the current directory**

```bash
$ vagrant init

or:

$ vagrant init boxname # get the box from https://atlas.hashicorp.com/boxes/search
```

**Add the box of your choice to your vagrant project**
```bash
$ vagrant box add boxname # example: vagrant box add hashicorp/precise64
```

**Get the list of all boxes of your vagrant projects**
```bash
$ vagrant box list
```

**Check outdated boxes of your vagrant projects**
```bash
$ vagrant box outdated
or:
$ vagrant box outdated --global
```

**Remove boxes from your vagrant projects**
```bash
$ vagrant box remove box_name
$ vagrant box remove box_name --provider # if a box has multiple providers
$ vagrant box remove box_name --box-version=version # example: vagrant box remove hashicorp/precise64 --box-version=2.2.1
$ vagrant box remove --all # remove all versions
$ vagrant box remove box_name --force # remove even an active vagrant environment
$ vagrant box remove box_name --provider= provider_name # example: vagrant box remove hashicorp/precise64 --provider=virtualbox
```

**Installing a plugin**
```bash
$ vagrant plugin install plugin_name #  from a known gem source
$ vagrant plugin install /path/to/plugin_name.gem # from a local file source
```

**Start your vagrant project**
```bash
$ vagrant up # first time it will provision & start your virtual machine
$ vagrant reload # e.g. after editing the Vagrantfile
```

**Log into your vagrant project**
```bash
$ vagrant ssh # by default username = vagrant, password = vagrant
```

**Provision your current vagrant project**
```bash
$ vagrant provision # this will setup your vagrant project based on the Vagrantfile and other files that is included in the Vagrantfile
or:

$ vagrant reload --provision
```

**Stop your current vagrant project**
```bash
$ vagrant suspend # this will stop and continue your VM at the point when you stopped the last time
$ vagrant halt # this will shut down your current virtual machine
```

## Clean up

**Get rid of the VM that is managed by your current vagrant project**

```bash
$ vagrant destroy
```

## Get infos

**Check the status of the current vagrant project**

```bash
$ vagrant status
```

**Check the status of all vagrant projects based on caching**

```bash
$ vagrant global-status # this will not verify invalid VMs, better add the --prune flag (see above)
```

**Prune invalid entries and list active vagrant projects**

```bash
$ vagrant global-status --prune
```

## Push

**Deploy your vagrant project to a server**

```bash
$ vagrant push # dependent on your config settings where to push
$ vagrant push server_environment # example: $ vagrant push staging
```

## Share

**Enable public accessible vagrant share session with anyone in the world**

```bash
$ vagrant share # it requires an account on https://atlas.hashicorp.com to generate URLs for HTTP-sharing
```

**Disable public accessible vagrant share session**

```bash
$ vagrant share --disable-http
```

**Disable your vagrant share session**

```bash
CTRL + C # break up the session or wait after default expiration period (1 hour)
```

**Use http-sharing for the vagrant share session**

```bash
$ vagrant share --http

and/or:

$ vagrant share --https
```

**Enable ssh for your vagrant share session**

```bash
$ vagrant share --ssh # Vagrant generates a new keypair for SSH access and will output the name of the share session
$ vagrant share --ssh-once # the generated key-pair will be destroyed after one connection attempt
$ vagrant connect --ssh name_of_the_share # Example: $ vagrant connect --ssh itty-bitty-polar-8667
```
