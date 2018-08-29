# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV["LC_ALL"] = "en_US.UTF8"

Vagrant.configure("2") do |config|
  (1..2).each do |i|
    config.vm.define "master#{i}" do |node|
      node.vm.box = "bento/centos-7.4"
      node.vm.hostname = "master#{i}"
      node.ssh.username = "root"
      node.ssh.password = "vagrant"
      node.ssh.insert_key = true
      node.vm.box_check_update = false
      node.vm.network "private_network", ip: "11.11.11.11#{i}"
      node.vm.provider "virtualbox" do |vb|
              vb.customize ["modifyvm", :id, "--name", "master#{i}", "--memory", "1024"]
      end
      node.vm.provision "shell", inline: <<-SHELL
        echo "Hello,enjoy!!"
      SHELL
      end
  end
end
