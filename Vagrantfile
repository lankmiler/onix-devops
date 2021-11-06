# -*- mode: ruby -*-
# vi: set ft=ruby :
 
# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
 
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.box = "centos/8"
 
  config.vm.network :private_network, ip: "192.168.234.131"
  config.vm.define "mysite.local"
  config.vm.hostname = "mysite.local"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provision "ansible_local" do |ansible|
  	ansible.playbook = "/vagrant/ansible/deploy.yml"
    ansible.raw_arguments = ["-i /vagrant/ansible/hosts -vvv"]
  end

  config.vm.provision "shell", path: "scripts/httpd_centos_fix.sh"
end