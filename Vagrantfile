# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.boot_timeout = 300
  config.vm.box_check_update = true 
  config.vm.network "public_network"
  config.vm.box_download_checksum = "aabcfe77a08b72bacbd6f05e5f26b67983b29314ee0039d0db4c9b28b4909fcd"
  config.vm.box_download_checksum_type = "sha256"
  config.vm.graceful_halt_timeout = 60
  config.vm.hostname = "bastionHost"
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  config.ssh.keep_alive = true
  #Just in Case:
  #https://www.vagrantup.com/docs/networking/private_network.html
  #config.vm.network "private_network", ip: "192.168.0.10"
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "Bastion Work Host"
    vb.memory = "512"
	#USB Issues
	vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
  end
  
  #Provisioning the VM
  config.vm.provision "shell", inline: <<-SHELL
    yum install -y -q -e 0 epel-release git vim
	yum update -y -q -e 0
	yum install -y -q -e 0 awscli putty
	#If you live in Brazil like me!
	localectl set-keymap br-abnt2
	timedatectl set-timezone America/Sao_Paulo
	#Generate/Import SSH Pub Key
	sudo -u vagrant ssh-keygen -t rsa -b 2048 -f /home/vagrant/.ssh/id_rsa -q -N ""
	sudo -u vagrant cat /home/vagrant/.ssh/id_rsa.pub > /home/vagrant/.ssh/authorized_keys
	sudo -u vagrant cp /home/vagrant/.ssh/id_rsa.pub /vagrant
	sudo -u vagrant puttygen /home/vagrant/.ssh/id_rsa -o /vagrant/winvagrantkey.ppk
  SHELL
end
