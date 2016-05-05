# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vbguest.no_remote = true
  config.vbguest.auto_update = false
 
  config.vm.define 'backup-server' do |server|
    server.vm.box = 'geerlingguy/centos7'
    server.vm.network :private_network, ip: "192.168.33.11"
  end

  config.vm.define 'backup-client' do |client|
    client.vm.box = 'geerlingguy/centos7'
    client.vm.network :private_network, ip: "192.168.33.12"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "setup.yml"
    ansible.groups = {
	"centos" => ["centos7","centos6"]
    }
  end
end
