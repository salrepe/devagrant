VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'debian'
  config.vm.box_url = 'http://f.willianfernandes.com.br/vagrant-boxes/DebianSqueeze64.box'
  config.berkshelf.enabled = true
  config.berkshelf.berksfile_path = File.join(File.dirname(__FILE__), 'Berksfile')
  config.omnibus.chef_version = :latest
  config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |vb|
    vb.customize ['modifyvm', :id, '--memory', '2048']
  end

  config.vm.network :private_network, :ip => '10.10.2.15', :netmask => '255.255.255.0'

  config.vm.provision :chef_solo do |chef|
    chef.custom_config_path = "Vagrantfile.chef"

    chef.add_recipe 'apt'
    chef.add_recipe 'ruby_build'
    chef.add_recipe 'rbenv::user'
    chef.add_recipe 'rbenv::vagrant'
    chef.add_recipe 'vim'
    chef.add_recipe 'postgresql'
    chef.add_recipe 'zsh'
    chef.add_recipe 'ack'

    chef.json = {
      rbenv: {
        user_installs: [{
          user: 'vagrant',
          rubies: ['2.1.2'],
          global: '2.1.2',
          gems: {
            '2.1.2' => [
              { name: 'bundler' }
            ]
          }
        }]
      },
    }
  end
end
