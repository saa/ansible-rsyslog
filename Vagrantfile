# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vbguest.no_remote = true
  config.vbguest.auto_update = false

  config.vm.define 'trusty' do |instance|
    instance.vm.box = 'ubuntu/trusty64'
  end
 
  config.vm.define 'centos7' do |instance|
    instance.vm.box = 'geerlingguy/centos7'
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "test.yml"
    ansible.verbose = 'v'
    ansible.sudo = true
  end
end
