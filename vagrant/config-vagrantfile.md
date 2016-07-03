## Vagrant (Part 3)

### Config the Vagrantfile

A `Vagrantfile` has the function to provision a project, means it will fetch all required software packages (that is defined by you) and install them for you before it boots the virtual machine.

To have an understanding of this chapter, please make sure to read [part 1](#vagrant/set-up-vagrant.md) and [part 2](#vagrant/install-software.md) first.

Given you have already set up your vagrant environment and have all required software packages installed, please open your `Vagrantfile`:

```
$ vim Vagrantfile
```

#### Now, copy the following code snippet example and paste it into the Vagrantfile. Remove all parts that are duplicates.

```
Vagrant.configure(2) do |config|
  config.vm.define "your_project_vm" do |box|
    box.vm.box = "ubuntu/trusty64"
    box.vm.hostname = "your_project.dev"
    box.vm.provision :shell, path: "bootstrap.sh"
end
```

Note: If you use the same vagrant box for multiple projects, it may cause conflicts, if you don't specify the vagrant box which is why it is recommended to set a `hostname` and define the box name (`your_project_vm`) for each project. At last, we tell vagrant to execute the script file `bootstrap.sh` for software packages installations.

#### Set the ssh forward-agent to `true` so you don't need to always paste your ssh-key in order to access and transfer data:

```
config.ssh.forward_agent = true
```

### Create a private network, which allows host-only access to the machine using a specific IP, for example:
```
config.vm.network "private_network", ip: "192.168.33.15"
```

Note: Use a different IP address for each of your projects to avoid access collisions.

#### This is optional but helpful, if you want to restrict access to specific ports only from vagrant:
```
config.vm.network "forwarded_port", guest: 4567, host: 4567, ip: "0.0.0.0", auto_correct: true 
```

Your vagrant project would be accessible here in the browser:
```
# => http://0.0.0.0:4567
```

#### Enable NFS (network file system) mounting:
```
config.vm.synced_folder "../your_project", "/home/vagrant/your_project", type: 'nfs'
```

Note: If you work on a project with a lot of data, using vagrant and the virtual machine (guest) may not be the best performance solution. If your project becomes very slow for each process, consider to enable NFS mounting, so you can share specific folders within your private network between the host (computer) and guest (virtual machine). Read more about it [here](https://friendsofvagrant.github.io/v1/docs/nfs.html).

#### Now reload the vagrant project with:
```
$ vagrant reload --provision
```

Your vagrant should boot your machine again. Congratulations, you're done for now! :)
