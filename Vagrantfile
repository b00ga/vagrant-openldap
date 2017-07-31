# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"

  config.vm.define 'client' do |machine|
      machine.vm.hostname = "somebox.example.com"
      machine.vm.network :private_network, ip: "10.0.0.100"
  end

  config.vm.define 'server' do |machine|
      machine.vm.hostname = "auth.example.com"
      machine.vm.network :private_network, ip: "10.0.0.10"

      machine.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbook.yml"
        ansible.inventory_path = "hosts"
        ansible.galaxy_role_file = "requirements.yml"
        ansible.limit = "all"
        ansible.verbose  = true
      end
  end

end
