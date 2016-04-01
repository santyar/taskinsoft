# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
 
 config.vm.define "nginx" do  |web|
   web.vm.box = "hashicorp/precise32"
   web.vm.network "private_network", ip: "192.168.3.2", virtualbox_intnet: "test"     
   web.vm.network "forwarded_port", guest: 80, host: 8082
   web.vm.provider "virtualbox" do |vb|
     vb.name = "Role"
     vb.memory = "512"
     vb.cpus = "1"
   end
 end
 config.vm.define "develop" do |py|
  py.vm.box = "hashicorp/precise32"
  py.vm.network "private_network", ip: "192.168.3.3", virtualbox_intnet: "test"
  py.vm.network "forwarded_port", guest: 22, host: 2020, id: "ssh"
  py.vm.provider "virtualbox" do |vb|
     vb.name = "dev"
     vb.memory = "512"
     vb.cpus = "1"
  end
 end 
 config.vm.provision "ansible" do |ansible|
  ansible.playbook = "playbook.yml"
  ansible.sudo = true 
 end
end
