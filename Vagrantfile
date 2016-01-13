# -*- mode: ruby -*-
# vi: set ft=ruby :
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "exeapps/snaplabs-backend"
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false
  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
#  config.vm.network "forwarded_port", guest: 2424, host: 2424
  config.vm.network "forwarded_port", guest: 2480, host: 2480
  config.vm.network "forwarded_port", guest: 5672, host: 5672
  config.vm.network "forwarded_port", guest: 15672, host: 15672
  config.vm.network "forwarded_port", guest: 6379, host: 6379
  config.vm.network "forwarded_port", guest: 60010, host: 60010
  config.vm.network "forwarded_port", guest: 4242, host: 4242  
  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"
  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"
  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "4096"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.
  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end
  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    su vagrant
   
	
	sudo echo "JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64" >> /etc/environment
	sudo echo "HBASE_HOME=/opt/hbase" >> /etc/environment
	source /etc/environment

	sudo chown -R vagrant:vagrant  /opt/hbase/bin/start-hbase.sh
	sudo chown -R vagrant:vagrant /opt/opentsdb/start.sh
	sudo chown -R vagrant:vagrant /opt/orientdb/start.sh 
	
	/opt/orientdb/start.sh
	/opt/hbase/bin/start-hbase.sh
	sleep 20
	/opt/opentsdb/start.sh
	
	
	env COMPRESSION=NONE /opt/hbase/create_tsdb_tables.sh
  SHELL
end
