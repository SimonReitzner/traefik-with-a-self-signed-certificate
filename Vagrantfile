# -*- mode: ruby -*-
# vi: set ft=ruby :

# This starts the Vagrant configuration block, using version 2 of the configuration format.
# Specifies the base box image to use for the virtual machine (VM).
Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  
  # Defines a VM named "vm" and starts its configuration block.
  config.vm.define "vm" do |vm|

    # Sets the hostname of the VM to "ubuntu-vm".
    # Configures a private network for the VM with the IP address constructed from the private_network variable.
    vm.vm.hostname = "ubuntu-vm"
    vm.vm.network "private_network", ip: ENV["VM_IP"]
    
    # Starts the provider-specific configuration.
    vm.vm.provider "virtualbox" do |vb|

      # Allocates 2048 MB of memory and 2 CPU.
      vb.memory = "2048"
      vb.cpus = 2
    end
  end

  # Adds an ansible_local provisioner
  config.vm.provision "ansible_local" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.playbook = "provision.yml"
  end
end
