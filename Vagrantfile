# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.ssh.username = "vagrant"
  config.ssh.forward_agent = true
  config.vm.provision :shell, :path => "vagrant_setup.sh", :privileged => false

  config.vm.define "pwn", primary: true do |u64|
    u64.vm.network "private_network", ip: "10.10.10.10"
    u64.vm.provider "virtualbox" do |vb, override|
      override.vm.box ="geerlingguy/ubuntu1604"
      # Sync a folder between the host and all guests.
      # Uncomment this line (and adjust as you like)
      #override.vm.synced_folder "~/code", "/code"

      vb.name = "pwn"
      vb.memory = "2048"
      vb.gui = false
    end
    u64.vm.provider "libvirt" do |lv, override|
      override.vm.box = "algebro/ubuntu1604"
      #override.vm.network "private_network", ip: "10.10.10.10"
      # Sync a folder between the host and all guests.
      # Uncomment this line (and adjust as you like)
      # NOTE: Requires installation of the nfs-server package on the host machine
      # If `vagrant up` hangs at Mounting NFS folders, modify your firewall configuration
      # to allow nfs, rpc, and mountd services     
      override.vm.synced_folder "~/ctf", "/ctf", :nfs => true
      lv.memory = "2048"
      lv.graphics_type = "none"
    end
  end
end
