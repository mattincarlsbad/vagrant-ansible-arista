Vagrant.configure(2) do |config|
  
  config.vm.define "leaf1" do |leaf1|
    leaf1.vm.box = "vEOS-lab-4.18.5M-virtualbox.box"
    leaf1.vm.box_url = "http://webserver.yourcompany.com/vEOS-lab-4.18.5M-virtualbox.box"
    leaf1.vm.boot_timeout = 3000
    # Internal networks for switchport interfaces.
    leaf1.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "sp1swp2-lf1swp2", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "sp2swp2-lf1swp3", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "lf1swp4-lf2swp4", auto_config: false
    leaf1.vm.network "private_network", virtualbox__intnet: "lf1swp5-lf2swp5", auto_config: false
    leaf1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    # Enable eAPI in the EOS config
    leaf1.vm.provision 'shell', inline: <<-SHELL
      FastCli -p 15 -c "configure
      username admin privilege 15 role network-admin secret admin
      hostname leaf1
      management api http-commands
      no shutdown
      interface eth1
      no switchport
      ip address 10.0.0.1 255.255.255.0
      exit"
    SHELL
  end

  config.vm.define "leaf2" do |leaf2|
    leaf2.vm.box = "vEOS-lab-4.18.5M-virtualbox.box"
    leaf2.vm.box_url = "http://webserver.yourcompany.com/vEOS-lab-4.18.5M-virtualbox.box"
    leaf2.vm.boot_timeout = 3000
    # Internal networks for switchport interfaces.
    leaf2.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "sp1swp3-lf2swp2", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "sp2swp3-lf2swp3", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "lf1swp4-lf2swp4", auto_config: false
    leaf2.vm.network "private_network", virtualbox__intnet: "lf1swp5-lf2swp5", auto_config: false
    leaf2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    # Enable eAPI in the EOS config
    leaf2.vm.provision 'shell', inline: <<-SHELL
      FastCli -p 15 -c "configure
      username admin privilege 15 role network-admin secret admin
      hostname leaf2
      management api http-commands
      no shutdown
      interface eth1
      no switchport
      ip address 10.0.0.2 255.255.255.0
      exit"
    SHELL
  end

  config.vm.define "spine1" do |spine1|
    spine1.vm.box = "vEOS-lab-4.18.5M-virtualbox.box"
    spine1.vm.box_url = "http://webserver.yourcompany.com/vEOS-lab-4.18.5M-virtualbox.box"
    spine1.vm.boot_timeout = 3000
    # Internal networks for switchport interfaces.
    spine1.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "sp1swp2-lf1swp2", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "sp1swp3-lf2swp2", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "swp4", auto_config: false
    spine1.vm.network "private_network", virtualbox__intnet: "swp5", auto_config: false
    spine1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    spine1.vm.provision 'shell', inline: <<-SHELL
      FastCli -p 15 -c "configure
      username admin privilege 15 role network-admin secret admin
      hostname spine1
      management api http-commands
      no shutdown
      interface eth1
      no switchport
      ip address 10.0.0.3 255.255.255.0
      exit"
    SHELL
  end

  config.vm.define "spine2" do |spine2|
    spine2.vm.box = "vEOS-lab-4.18.5M-virtualbox.box"
    spine2.vm.box_url = "http://webserver.yourcompany.com/vEOS-lab-4.18.5M-virtualbox.box"
    spine2.vm.boot_timeout = 3000
    # Internal networks for switchport interfaces.
    spine2.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "sp2swp2-lf1swp3", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "sp2swp3-lf2swp3", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "swp4", auto_config: false
    spine2.vm.network "private_network", virtualbox__intnet: "swp5", auto_config: false
    spine2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
      vb.customize ["modifyvm", :id, "--nicpromisc6", "allow-all"]
    end
    spine2.vm.provision 'shell', inline: <<-SHELL
      FastCli -p 15 -c "configure
      username admin privilege 15 role network-admin secret admin
      hostname spine2
      management api http-commands
      no shutdown
      interface eth1
      no switchport
      ip address 10.0.0.4 255.255.255.0
      exit"
    SHELL
  end

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "ubuntu/xenial64"
    ansible.vm.network "private_network", virtualbox__intnet: "mgmt", auto_config: false
    ansible.vm.provision "shell", inline: <<-SHELL
     sudo ifconfig enp0s8 10.0.0.20/24
     sudo apt-get update
     sudo apt-get install git vim python-netaddr python-pip sshpass -y
     sudo pip install ansible
     git clone https://github.com/mattincarlsbad/ansible-arista-training-vagrant
     git clone https://github.com/mattincarlsbad/ansible-arista-show-commands
    SHELL
  end
  
end
