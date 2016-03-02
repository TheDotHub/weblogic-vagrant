Vagrant.configure(2) do |config|
  ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

  config.vm.box = "jeqo/oracle-database-11g-se-ol7"
  config.vm.hostname = "host"

  config.vm.network :private_network, ip: "192.168.56.10"

  config.vm.network "forwarded_port", guest: 1521, host: 1521

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 1
    vb.memory = "1500"
    vb.name = "local-osi-db"
    vb.gui = "true"
  end

  config.vm.provision "shell", inline: "cd /vagrant && ansible-galaxy install -f -p ./roles -r roles.yml"

  config.vm.provision "shell", inline: "cd /vagrant && ansible-playbook main.yml -c local"

end
