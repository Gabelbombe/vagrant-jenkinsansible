# -*- mode: ruby -*-
# vi: set ft=ruby :
## Based roughly around: https://github.com/rgl/jenkins-vagrant

Vagrant.configure("2") do | config |
  config.vm.box = "ehime/ubuntu1604" ##tbd

  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :virtualbox do | v |
    v.name = "jenkins"
    v.memory = 512
    v.cpus = 2
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.hostname = "jenkins"
  config.vm.network :private_network, ip: "192.168.33.55"

  ## Set the name of the VM
  config.vm.define :jenkins do | jenkins |
    ##oikology
  end

  ## Ansible provisioner
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.sudo = true
  end

end
