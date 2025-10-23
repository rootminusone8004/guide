# vagrant

## Introduction
Vagrant is a virtualbox management system that is used to automate the creation of VMs easily. It can also maintain multiple VMs at the same time.

All the details are kept in a **ruby** file call **Vagrantfile**. All confgurations and software details are kept there. Then with just a single command all the VMs will be created on top the physical machine.

These created VMs are ready to work. In vagrant, VMs are called **boxes**.

### vagrant file

In a vagrant file, three important things are made clear. They are:
- Which *provider* to use:
  - VirtualBox
  - VMWare
  - AWS cloud
  - Google cloud
  - Azure
  - OpenStack
- which base **image** to use
- which **provisioner** to use:
  - Ansible
  - Puppet
  - Chef
  - Salt
  - Scripts

## Installation
Installation command here is shown for **Debian and its derivatives**.
``` bash
sudo apt install vagrant
```

Also you can follow download the software [here](https://developer.hashicorp.com/vagrant/install?product_intent=vagrant).

Check if vagrant is installed:
``` bash
vagrant --version
```

## create a new VM
- create a new folder for vagrant project
- navigate to the folder and create a vagrant file with:

  ```bash
  vagrant init
  ```
- choose a box from https://portal.cloud.hashicorp.com/vagrant/discover.
- add configuration of the box in vagrantfile.

  > **note**: We can also create vagrantfile directly like this:
  ``` bash
  vagrant init centos/stream8 --box-version 20230710.0
  ```
- finally run the VM with the command:
  ``` bash
  vagrant up
  ```
- connect to your vagrant box CLI via ssh
  ``` bash
  vagrant ssh
  ```
  > **note**: Vagrantfile can also be generated online from https://vagrantfile-generator.vercel.app
- go to the page
- give the credentials
- generate the config file and thats it!

## important basic commands
### vagrant box commands

Get the basic tips
``` bash
vagrant box --help
```

Add a box to your local box repository
``` bash
vagrant box add ubuntu/focal64
```

List all the boxes in the local repository
``` bash
vagrant box list
```

Check if any vagrant box is outdated
``` bash
vagrant box outdated
```

Update the box to a new version
``` bash
vagrant box update
```

Repackage a box with a new name and metadata
``` bash
vagrant box repackage ubuntu/focal64 --name my-new-box
```

Remove outdated boxes from the local repository
``` bash
vagrant box prune
```

Remove a box from the local repository
``` bash
vagrant box remove centos/7
```

### vagrant commands

initialize a new Vagrant environment by creating a Vagrantfile
``` bash
vagrant init
```

Create and configure the guest machine
``` bash
vagrant up
```

Log in to the guest machine via SSH
``` bash
vagrant ssh
```

Configure OpenSSH to make a valid configuration to connect to VMs
``` bash
vagrant ssh-config
```

Stop the guest machine
``` bash
vagrant halt
```

Suspend the guest machine
``` bash
vagrant suspend
```

Resume the suspended guest machine
``` bash
vagrant resume
```

Reload the guest machine by restarting it
``` bash
vagrant reload
```

Stop and delete all traces of the guest machine
``` bash
vagrant destroy --force
```

Show the status of the current Vagrant environment
``` bash
vagrant status
```

Show the system wide vagrant status
``` bash
vagrant global-status
```

Package a running virtual environment into a reusable box
``` bash
vagrant package --output mybox.box
```

Run any configured provisioners against the running VM
``` bash
vagrant provision
```

Install a Vagrant plugin
``` bash
vagrant plugin install myplugin
```

List all installed vagrant plugins
``` bash
vagrant plugin list
```

Uninstall a vagrant plugin
``` bash
vagrant plugin uninstall myplugin
```

## provision a VM

### within Vagrantfile
- Open Vagrantfile and add config.vm.provision block, add it to your Vagrantfile.
- Choose a provisioner. Vagrant supports several provisioners, including shell, Ansible, Puppet and Chef
``` ruby
config.vm.provision "shell", inline: <<-SHELL
  # add your commands here
  sudo apt update
  sudo apt install -y neofetch
SHELL
```
- save Vagrantfile and start virtual machine.
> **Note**: After saving the file, you can apply those changes by this command:
  ``` bash
  vagrant provision
  ```

### in a separate file
- Create a new file (e.g. provision.sh) and add the scripts to provision the VM.
- Give the path of script in the Vagrantfile
  ``` ruby
  config.vm.provision :shell, path: "provision.sh"
  ```
## vagrant network configuration

Networking allows access to the Virtual Machine from outside (like from host system).<br>
Vagrant by default forwards port 22 from the guest machine (VM) to an open port in the host machine.<br>
You can also forward a specific port of your choice using vagrantfile.
Follow the below steps:
- Open vagrantfile and add this line:
  ``` ruby
  config.vm.network "forwarded_port", guest: 80, host: 8080
  ```
Here is the example:
``` ruby
config.vm.box = "centos/7"
config.vm.provision :shell, path: "provision1.sh"
config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
# auto_correct is helpful when port 8080 is busy
end
```

You can also use static IP address.
``` ruby
config.vm.network "private_network", ip: "192.168.56.10"
```

You can also use bridged adapter.
``` ruby
config.vm.network "public_network", bridge: "wlp2s0"
```

Users can now access the webserver running in VM by navigating to http://localhost:8080 on your host machine.

- Add provision script to install and start Apache Server on the VM
- Restart VM with uploaded Vagrantfile
``` bash
vagrant reload --provision
```

> **note**: *auto_correct* will choose from port 2200 to 2250. But you can choose any custom port range as well.

Here is the example:
``` ruby
config.vm.box = "centos/7"
config.vm.provision :shell, path: "provision1.sh"
config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
config.vm.usable_port_range = (2200..2250)
end
```

## share folder between host and guest

Usually the guest VM has the contents of the host machine's folder where the Vagrantfile is located. It is in the <u>/vagrant</u> directory of guest machine.

New files will appear when a vagrant reload is performed.
If you want to change the default folder setting, uncomment *config.vm.synced_folder* line.

## take snapshots of VM
### introduction

Snapshot is a full copy of the VM in its current state.
All configurations - disk contents, apps, packages, folders, memory are preserved.
Acts as a backup of the VM.
Restoring the VM from an earlier state.

The following command saves the current state of VM:
``` bash
vagrant snapshot save my_snapshot
```
The location of snapshots will be the same folder where vagrantfile is. It is in a hidden folder.

_note_: you can also get help about snapshots
``` bash
vagrant snapshot --help
```

### more commands related to snapshots

list all the snapshots
``` bash
vagrant snapshot list
```
restore the machine from an earlier snapshot
``` bash
vagrant snapshot restore my_snapshot
```
delete the snapshot
``` bash
vagrant snapshot delete my_snapshot
```

## plugins

Plugins are add-ons to enhance functionality of a tool.
Plugins for vagrant can be found [here](https://github.com/hashicorp/vagrant/wiki/Available-Vagrant-Plugins). Also the instructions of using a plugin can also be found there.

Plugins are stored in <u>~/.vagrant.d/</u> directory.

### plugin commands

see subcommands and options
``` bash
vagrant plugin --help
```

list all the installed plugins
``` bash
vagrant plugin list
```

install a plugin
``` bash
vagrant plugin install <plugin_name>  # vagrant plugin install vbinfo
```

use the plugin
``` bash
vagrant <plugin_name>
```

update a plugin
``` bash
vagrant plugin update <plugin_name>
```

repair installed plugins in case of error
``` bash
vagrant plugin repair
```

associate the plugin with a license file if needed
``` bash
vagrant plugin license <license_file>
```

remove a plugin
``` bash
vagrant plugin uninstall <plugin_name>
```

delete ALL plugins
``` bash
vagrant plugin expunge
```
 
reinstall all the expunged plugins
``` bash
vagrant plugin expunge --reinstall
```