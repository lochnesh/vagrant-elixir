# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise32"

  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  config.vm.network :forwarded_port, guest: 80, host: 8080

  config.vm.synced_folder "~/projects/", "/home/vagrant/projects/"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.json = {
      "elixir" => {
        "elixir_git_ref" => "v0.14.0"
      },
       "erlang" => {
        "otp_git_ref" => "OTP-17.0"
      }
    }
    chef.add_recipe "apt::default"
    chef.add_recipe "erlang"
    chef.add_recipe "elixir"
  end
end
