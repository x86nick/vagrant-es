# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |data|
  data.vm.box = "ubuntu/trusty64"
  data.vm.network "private_network", ip: "10.10.10.10"
  data.librarian_chef.cheffile_dir = "data"
  data.vm.provision "chef_solo" do |chef|
    chef.cookbooks_path = "data/cookbooks"
    chef.add_recipe "apt"
    chef.add_recipe "java"
    chef.add_recipe "sonarqube"
    chef.json = {
      "java" => {
        "jdk_version" => "8"
      },
    }
  end
end
