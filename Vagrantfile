# -*- mode: ruby -*-
# vi: set ft=ruby :

MEMORY_DEFAULT = 512

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "influx"

  config.vm.provider :virtualbox do |v|
    v.memory = MEMORY_DEFAULT
  end

  config.vm.provider :vmware_fusion do |v|
    v.vmx["memsize"] = MEMORY_DEFAULT
  end

  config.vm.network "forwarded_port", guest: 8083, host: 8083, auto_correct: true
  config.vm.network "forwarded_port", guest: 8086, host: 8086, auto_correct: true
  config.vm.network "forwarded_port", guest: 8088, host: 8088, auto_correct: true

  config.vm.provision :shell, inline: "apt-get purge -qq -y --auto-remove chef puppet"
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "site.yml"
  end
end
