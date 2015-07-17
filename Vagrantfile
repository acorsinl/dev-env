# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.hostname = "tamagotchi"
  config.vm.synced_folder "/Users/acorsinl/Documents/Workspace/Code/bin", "/opt/bin"
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
    v.customize ["modifyvm", :id, "--cpus", "2"]
  end
  config.vm.provision :ansible do |ansible|
    #ansible.inventory_path = "./hosts"
    ansible.groups = {
      "webservers" => ["default"],
      "microservices" => ["default"],
      "mysqlservers" => ["default"],
      "mongoservers" => ["default"],
      "lbservers" => ["default"]
    }
    ansible.playbook = "playbook.yml"
  end
end
