# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.forward_agent = true

  config.vm.define :ferret do |ferret|
    ferret.vm.provider :virtualbox do |vm|
      vm.customize ["modifyvm", :id, "--cpus", 2]
      vm.customize ["modifyvm", :id, "--memory", 2048]
      vm.customize ["modifyvm", :id, "--name", "ferret"]
    end

    ferret.vm.box = "ubuntu/xenial64"
    ferret.vm.hostname = "ferret"

    ferret.vm.network :private_network, ip: "10.128.0.5"

    ferret.vm.provision "shell" do |shell|
      shell.inline = "apt-get install -y python"
    end

    ferret.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yaml"
    end
  end

end