require 'rbconfig'
require 'yaml'
inventory = YAML.load_file("my_inventory.yml")


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"
  
  config.vm.synced_folder ".", "/vagrant", mount_options: ["dmode=775,fmode=600"]

  config.vm.define "node1" do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["node1"]["ansible_ssh_host"]
	machine.vm.provider "virtualbox" do |vbox|
		vbox.memory = "1024"
		vbox.cpus = "1"
		vbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		vbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
	end
  end

  config.vm.define "node2" do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["node2"]["ansible_ssh_host"]
	machine.vm.provider "virtualbox" do |vbox|
		vbox.memory = "1024"
		vbox.cpus = "1"
		vbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		vbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
	end
  end
  
  config.vm.define "node3" do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["node3"]["ansible_ssh_host"]
	machine.vm.provider "virtualbox" do |vbox|
		vbox.memory = "1024"
		vbox.cpus = "1"
		vbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		vbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
	end
  end

  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["controller"]["ansible_ssh_host"]
	machine.vm.provider "virtualbox" do |vbox|
		vbox.memory = "1024"
		vbox.cpus = "1"
		vbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		vbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
	end

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "CassandraCluster.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all" # or only "nodes" group, etc.
      ansible.inventory_path = "my_inventory.yml"
    end
  end

end