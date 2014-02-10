# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise32"

  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  config.vm.network :forwarded_port, guest: 80, host: 8080

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apt::default"
    chef.add_recipe "erlang"
  end
end
