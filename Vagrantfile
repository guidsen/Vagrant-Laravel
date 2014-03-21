# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax versie. Niet wijzigen!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "precise32"
    config.vm.box_url = "http://files.vagrantup.com/precise32.box"
    #config.vm.network :forwarded_port, guest: 80, host: 8080
    config.vm.provision :shell, :path => "install.sh"

    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.hostmanager.ignore_private_ip = false
    config.hostmanager.include_offline = true

    config.vm.define 'webserver' do |node|
        # De hostname is de url van je server.
        node.vm.hostname = "guido.dev"
        node.vm.network :private_network, ip: '192.168.42.42', host: 8080
    end

    config.vm.synced_folder "www/", "/vagrant/www", :mount_options => ["dmode=777", "fmode=666"]

end
