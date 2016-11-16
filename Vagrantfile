# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.ssh.username = "vagrant"
  config.ssh.forward_agent = true
  config.vm.provision :shell, :path => "vagrant_setup.sh", :privileged => false
  # Sync a folder between the host and all guests.
  config.vm.synced_folder "~/code", "/code"

  config.vm.define "pwn", primary: true do |u64|
    u64.vm.box = "ubuntu/xenial64"
    u64.vm.network "private_network", ip: "10.10.10.10"
    u64.vm.provider "virtualbox" do |vb|
      vb.name = "pwn ubuntu"
      vb.memory = "2048"
      vb.gui = false
    end
  end

  config.vm.define "pwn32", autostart: false do |u32|
    u32.vm.box = "ubuntu/xenial32"
    u32.vm.network "private_network", ip: "10.10.10.11"
    u32.vm.provider "virtualbox" do |vb|
      vb.name = "pwn ubuntu32"
      vb.memory = "1024"
      vb.gui = false
    end
  end

end
