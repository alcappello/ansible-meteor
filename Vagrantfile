VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

  config.vm.synced_folder "./", "/vagrant", :mount_options => ['dmode=777', 'fmode=777'] #, :nfs=>true

  config.vm.network "forwarded_port", guest: 80, host: 8080,
    auto_correct: true

  config.vm.network :forwarded_port, guest: 22, host: 2201, id: "ssh", auto_correct: true

  config.vm.define 'ansible-meteor' do |node|
    node.vm.hostname = 'ansible-meteor.dev'
    node.vm.network :private_network, ip: '192.168.99.195'
  end

  config.vm.provider :virtualbox do |v|
      # Set the timesync threshold to 10 seconds, instead of the default 20 minutes.
      v.customize ["guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/--timesync-set-threshold", 10000]
  end

  config.vm.provider :virtualbox do |v|
      v.memory = 2048
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "devtools/ansible/playbook.yml"
  end
end
