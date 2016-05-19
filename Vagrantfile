# -*- mode: ruby -*-
# vi: set ft=ruby :
$install_chef = <<SCRIPT
sudo apt-get update
sudo apt-get install -y curl
curl -L https://www.opscode.com/chef/install.sh | sudo bash
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 1
  end

  config.vm.provision "shell", :inline => $install_chef
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]
    chef.add_recipe 'git'
  end

  config.vm.provision "docker"
  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", run: "always"
end
