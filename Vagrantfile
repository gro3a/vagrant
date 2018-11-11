# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.define "devops-vagrant" do |config|
	
		config.vm.provider :digital_ocean do |provider, override|
			override.ssh.private_key_path = '~/.ssh/id_rsa'
			override.vm.box = 'digital_ocean'
			override.vm.box_url = 'https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box'
			override.nfs.functional = false
			config.env.enable
			provider.token = ENV['TOKEN']
			provider.image = 'ubuntu-16-04-x64'
			provider.region = 'nyc1'
			provider.size = '512mb'
		end
		config.vm.synced_folder '.', '/vagrant', disabled: true

		config.vm.provision 'ansible' do |ansible|
			ansible.playbook = 'goapp.yml'
		end
	end
  
end
