# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # VirtualBox Scientific Linux 6.5 minimal virtual machine template 
  config.vm.box = "SL-65-x86_64-minimal"
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/49910137/scientific65_x86_64_minimal.box"
  config.vm.synced_folder "ansible", "/home/vagrant/ansible"

  # We'll use ansible itself dor the initial provisioning of the head node 
  # to save tutorial time when updating repos etc.
  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "bootstrap/playbook.yml"
  end

  config.vm.provider :virtualbox do |vb|
  #    # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "360"]
      vb.memory=512
  end

  # headnode
  config.vm.define "headnode" do |headnode|
	headnode.vm.hostname = "headnode"
	headnode.vm.network "private_network", ip: "192.168.100.100"
	headnode.vm.network "private_network", ip: "10.100.100.1", netmask:"255.255.0.0"
	#headnode.vm.provision "shell", inline:"postinstall.sh"
	#headnode.vm.synced_folder "scratch", "/home/vagrant/scratch"
  end

  config.vm.define "node1" do |node1|
	node1.vm.hostname = "node1"
	node1.vm.network "private_network", ip: "10.100.101.1", netmask:"255.255.0.0"
  end
  
  config.vm.define "node2" do |node2|
	node2.vm.hostname = "node2"
	node2.vm.network "private_network", ip: "10.100.101.2", netmask:"255.255.0.0"
  end

  config.vm.define "node3" do |node3|
	node3.vm.hostname = "node3"
	node3.vm.network "private_network", ip: "10.100.101.3", netmask:"255.255.0.0"
  end

end
