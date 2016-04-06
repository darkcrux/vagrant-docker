# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  docker_host = ENV['DOCKER_HOST']

  ip_address = docker_host.match(/(\d{1,3}\.){3}\d{1,3}/)[0] unless docker_host.nil?
  ip_address ||= '20.20.20.20'

  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: ip_address

  config.vm.provider :virtualbox do |vb|
    vb.memory = 2048
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = 'provision/docker.yml'
  end

end
