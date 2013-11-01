# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  # Set box configuration
  config.vm.box = 'precise32'
  config.vm.box_url = 'http://files.vagrantup.com/precise32.box'

  # Assign this VM to a host-only network IP, allowing you to access it via the IP.
  config.vm.network :hostonly, '55.55.55.20'
  config.vm.forward_port 80, 5520
  config.vm.forward_port 3306, 5522
  
  # Share an additional folder to the guest VM. The first argument is
  # an identifier, the second is the path on the guest to mount the
  # folder, and the third is the path on the host to the actual folder.
  config.vm.share_folder 'www', '/var/www', 'www', mount_options: ['dmode=777','fmode=777']
  
  config.ssh.forward_agent = true

  # Enable provisioning with chef solo, specifying a cookbooks path (relative
  # to this Vagrantfile), and adding some recipes and/or roles.
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = 'cookbooks'
    chef.data_bags_path = 'data_bags'
    chef.add_recipe 'vagrant_main'

    chef.json.merge!({
      apache: {
        www_root: '/var/www'
      },
      mysql: {
        server_root_password: 'vagrant',
      }
    })
  end
end
