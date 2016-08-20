Vagrant.configure('2') do |config|
  config.vm.box = 'vagrant-ubuntu'
  config.vm.box_url = 'http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box'

  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network :forwarded_port, host: 10022, guest: 22
  config.vm.network :forwarded_port, host: 10080, guest: 80
  config.vm.provider :virtualbox do |vb|
     vb.gui = false
     vb.customize ['modifyvm', :id, '--memory', '1024']
     vb.customize ['modifyvm', :id, '--cpus', '1'] 
     vb.customize ['modifyvm', :id, '--ioapic', 'on']
   end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
  end
end
