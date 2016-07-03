# Vagrant (Part 2)

## Install Software

After following the tutorial how to set up vagrant [here](#vagrant/set-up-vagrant.md) in this chapter you will learn how to set up another file that will install all the software dependencies suited to your current project.

Before we start, please make to be in the `vagrant project root`. Go back to [part 1](#vagrant/set-up-vagrant.md) in case you need to read more about it.

Your structure should look like this:
```
vagrant
├── Vagrantfile
```
#### Create a script file that will contain all installation dependencies, e.g.:
```
$ touch bootstrap.sh
```

Your structure should look like this:
```
vagrant
├── Vagrantfile
├── bootstrap.sh
```

#### Open the `bootstrap.sh` with the editor of your choice, for example:
```
$ vim bootsrap.sh
```

#### Tell the script to execute `bash` as your shell by putting following `shebang` line on top of the file:
```
#!/usr/bin/env bash
```

#### Add following encoding line under the shebang line:**
```
$ locale-gen LC_ALL=en_US.utf8
```

If you want to know more about `locale`, read more [here](https://help.ubuntu.com/community/Locale)

Before we start with install instructions, you need to know following:

Usually you need root access when executing config installations, this means you would need to prepend `sudo` to`$ apt-get install software` but in the `bootstrap.sh` it is not required.

The flag `-y` stands for `yes` and saves a bit time, otherwise you would always have to confirm an installation processes.

#### Set up all core essentials to start with Ubuntu
```
$ apt-get update # this will fetch the latest index updates
$ apt-get install -y git vim curl wget unzip build-essential python-software-properties zsh
```

#### Set up essential library packages
```
$ apt-get install -y zlib1g-dev libssl-dev libreadline-dev libyaml-dev libxml2-dev libxslt1-dev libc url4-openssl-dev libffi-dev
```

#### Set up NFS mount (for better performance of synced folders between computer and virtual machine):
```
$ apt-get update
$ apt-get install -y nfs-kernel-server # host
$ apt-get install -y nfs-common portmap # client
```

#### Set up a http-server:
```
$ apt-get install -y apache2
```
or:
```
$ apt-get install -y nginx
```

#### Set up a database
```
$ apt-get install -y libmysqlclient-dev mysql-server
```
or:
```
$ apt-get install -y postgresql postgresql-client
```
or:
```
$ apt-get install -y libsqlite3-dev sqlite3
```
