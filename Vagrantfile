# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/trusty64'
  config.vm.synced_folder './app', '/vagrant', type: 'nfs'

  virtual_machines = {
    'tasukuforce' => '10.11.12.13'
  }

  virtual_machines.each do |hostname, ip|
    config.vm.define hostname do |host|
      host.vm.network :private_network, ip: ip
      host.vm.hostname = "#{hostname}.wordpress.dev"
    end

    config.vm.provider 'virtualbox' do |vb|
      vb.name = hostname
      vb.memory = 1024
      vb.cpus = 1
    end
  end
end