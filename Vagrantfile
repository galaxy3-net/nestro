# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "linux" do |linux|
      linux.vm.box = "cybersecurity/linux-scavenger"
      linux.ssh.insert_key = false
      linux.vm.network "private_network", ip: "192.168.200.105"
      linux.vm.synced_folder ".", "/vagrant", disabled: true
      config.vm.ignore_box_vagrantfile = true

	  config.trigger.after :up do |trigger|
    	trigger.name = "Complete Setup"
	  	trigger.info = File.read("Description")
	  end

	config.vm.synced_folder "../../Downloads", "/Downloads", owner: "1001", group: "1001", mount_options: ["fmode=777", "dmode=777"], create: true

      linux.vm.provider "virtualbox" do |vb| # specify hyper v vm
        vb.memory = 1024
        vb.cpus = 1
    	vb.customize ["modifyvm", :id, "--description", File.read("Description")]
      end
    end
  end