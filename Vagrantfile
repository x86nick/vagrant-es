# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |data|
  data.vm.box = "ubuntu/trusty64"
  data.vm.network "private_network", ip: "10.10.10.10"
  data.librarian_chef.cheffile_dir = "dataes"
  data.vm.provision "chef_solo" do |dataes|
    dataes.cookbooks_path = "chef/cookbooks"
    dataes.add_recipe "apt"
    dataes.add_recipe "java"
    dataes.add_recipe "elasticsearch"
    dataes.json = {
      "java" => {
        "jdk_version" => "8"
      },
      "elasticsearch" => {
        "version" => "5.0.0",
        "deb_url" => "https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.0.0.deb",
        "deb_sha" => "c4cac535f834f42676b182462120e5ffd69db513"
      }
    }
  end
end
