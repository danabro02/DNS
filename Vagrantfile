Vagrant.configure("2") do |config|
  
  config.vm.box = "debian/bookworm64"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y bind9
  SHELL

  config.vm.define "venus" do |venus|
    config.vm.provision "shell", inline: <<-SHELL

    cp /home/vagrant/compartida/named.conf.local /etc/bind/named.conf.local
    cp /home/vagrant/compartida/named.conf.options /etc/bind/named.conf.options
    cp /home/vagrant/compartida/db.192.168.57 /etc/bind/db.192.168.57
    cp /home/vagrant/compartida/db.sistema.test /etc/bind/db.sistema.test

    SHELL

    venus.vm.network "private_network", ip: "192.168.57.102"
  end

  config.vm.define "tierra" do |tierra|
    config.vm.provision "shell", inline: <<-SHELL

      cp /home/vagrant/compartida/named.conf.local.venus /etc/bind/named.conf.local

      SHELL

    tierra.vm.network "private_network", ip: "192.168.57.103"
  end
end
