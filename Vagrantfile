# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
   config.vm.define "server1", primary:true do |server1|
  server1.vm.box = "ubuntu/trusty64"
  server1.vm.network "private_network", ip: "192.168.33.10"

  server1.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
	 sudo apt-get dist-upgrade
     #sudo apt-get install -y apache2
	 sudo apt-get install -y php5
	 #debconf-utils is used to tell mysql the password.
	 #sudo apt-get install debconf-utils -y
	 #sudo debconf-set-selections <<< "mysql-server mysql-server/root_password password 1234"
	  #sudo debconf-set-selections <<< "mysql-server mysql-server/root_password_again password 1234"
	  #sudo apt-get install mysql-server -y
	  
   SHELL
end

 config.vm.define "server2" do |server2|
      server2.vm.box = "ubuntu/trusty64"
	 server2.vm.hostname ="server2"
	  server2.vm.network "private_network", ip: "192.168.33.20"
	  server2.vm.network "forwarded_port", guest:80, host:8080
	  #web.vm.network "public_network", ip: "192.168.1.131"
	  server2.vm.synced_folder "src/" , "/home/vagrant"
	  
	  
end
     
	 config.vm.define "server3" do |server3|
       server3.vm.box= "nrel/CentOS-6.5-x86_64"
       server3.vm.hostname ="server3"
       server3.vm.network "private_network", ip: "192.168.33.30"
	  # db.vm.network "public_network", ip: "192.168.1.131"
 end
 end