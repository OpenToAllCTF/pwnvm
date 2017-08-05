# PWNVM

This is an attempt to make it super easy to get set up with a VM you can use to play CTFs.

## Installation
1. Install a hypervisor. The following hypervisors are supported:
   * VirtualBox (default, recommended)
   * libvirt (requires vagrant-libvirt provider [here](https://github.com/vagrant-libvirt/vagrant-libvirt))
2. Install Vagrant:
   * OSX: `brew cask install vagrant`
   * Linux: `sudo apt-get install vagrant`
3. Clone this project and `cd` to clone dir.
4. Build VM and provision: `vagrant up`

### Note
If you're on a Debian-based system and receive a "no usable providers" error, uninstall vagrant, download the .deb package from the official website and install it.

`sudo apt-get remove vagrant`

`wget https://releases.hashicorp.com/vagrant/1.9.1/vagrant_1.9.1_x86_64.deb && sudo dpkg -i vagrant*`

## Usage
`vagrant ssh`

### File sharing
By default the directory that contains the _Vagrantfile_ is shared with the vm and is mounted at _/vagrant_, so you can move files between the host and guest by simply moving files to/from there.

### Services
The VM exposes its IP on a private network on ip 10.10.10.10. That means that you can run whatever services you like on the VM and they will be accessible from the host through that IP.

### Managing VMs
You should never have to open VirtualBox to manage the VMs. Everything can be done through `vagrant`, but must be done from the directory where the _Vagrantfile_ lives.

* See VMs: `vagrant global-status`
* Reprovision: `vagrant provision [<vm>]`
* SSH: `vagrant ssh [<vm>]`
* Adopt changes to _Vagrantfile_: `vagrant reload [<vm>]`
* Bring down VM: `vagrant halt [<vm>]`
* Bring up VM: `vagrant up [<vm>]`
* Scrap VM: `vagrant destroy [<vm>]`

## 32 bit VM
Although the 64-bit linux vm should be able to do whatever you need, you can also set up a 32 bit version. To do this, simply do `vagrant up pwn32`. The 64-bit (default) VM is named simply "pwn".
