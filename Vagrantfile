# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.provision 'file', source: '~/.ssh/id_rsa.pub', destination: '~/.ssh/my_key.pub'
  config.vm.provision 'shell', inline: 'cat /home/vagrant/.ssh/my_key.pub > /root/.ssh/authorized_keys'

  config.vm.box = 'ubuntu/trusty64'
  config.vm.synced_folder './app', '/vagrant', type: 'nfs'

  virtual_machines = {
    'tasukuforce' => '10.0.0.100'
  }

  virtual_machines.each do |hostname, ip|
    config.vm.define hostname do |host|
      host.vm.network :private_network, ip: ip
      host.vm.hostname = "#{hostname}.wordpress.dev"
    end
  end
end