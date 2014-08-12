# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "tifa"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  config.vm.network "private_network", ip: "192.168.100.2"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder "../../byng-systems@github.com/ferenda", "/opt/www", nfs: true
  config.vm.synced_folder "../../", "/home/vagrant/git", nfs: true

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/ansible/site.yml"
    # ansible.verbose = "vvvv"
  end
end
