# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX_NAME = 'xbp-nodejs-01031-x64'
PRECISE64_BOX_URL = 'https://s3-us-west-1.amazonaws.com/boxes.redtail/xbp-nodejs-01031-x64.box'

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = BOX_NAME
  config.vm.box_url = PRECISE64_BOX_URL

  # Forward local ssh credentials
  config.ssh.forward_agent = true

  # Setup netowrking and port forwarding
  config.vm.hostname = "test.local"
  config.vm.network 'private_network', ip: '10.33.33.200'
  config.vm.network 'forwarded_port', guest: 3000, host: 3000

  config.vm.synced_folder '.', '/vagrant', id: 'vagrant-root', disabled: true
  config.vm.synced_folder ".", "/home/vagrant/angular",  nfs: true

  config.vm.provider :virtualbox do |vb|
      vb.customize ['modifyvm', :id, '--memory', 1024]
      vb.customize ['modifyvm', :id, '--natdnsproxy1', 'off']
      vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'off']
  end
  # Use vagrant-bindfs to re-mount folder
  # config.bindfs.bind_folder "/vagrant-nfs", "/opt/xoom/apps/testharness/current"
  # config.vm.provision :puppet do |puppet|
    # puppet.facter = {
    #   'user' => 'vagrant',
    #  'fqdn' => 'testharness.development',
    #   'application_environment' => 'development',
    #   'manage_source' => false
    # }
    # puppet.manifests_path = 'puppet/manifests'
    # puppet.module_path = 'puppet/modules'
    # puppet.manifest_file  = 'site.pp'
    # puppet.options        = '--verbose'
  # end
end
