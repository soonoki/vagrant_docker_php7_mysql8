# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_url = "https://app.vagrantup.com/centos/boxes/7"  # ←この行を追加
  config.vm.box = "centos/7"
  config.vm.box_version = "1905.1"
  config.vm.synced_folder "./docker", "/home/vagrant/docker", create:true, owner: "vagrant", group: "vagrant", type: 'virtualbox', mount_options: ['dmode=777','fmode=777']
  config.vm.synced_folder "./docker/docker/mysql", "/home/vagrant/docker/docker/mysql", create:true, owner: "vagrant", group: "vagrant", type: 'virtualbox', mount_options: ['dmode=777','fmode=755']
  
  config.vm.network "private_network", ip: "192.168.33.50"

  config.vm.provision "shell", inline: <<-SHELL
      sudo yum -y update
      sudo yum remove -y docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-selinux docker-engine-selinux docker-engine
      sudo yum install -y yum-utils device-mapper-persistent-data lvm2
      sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
      sudo yum install -y docker-ce
      sudo usermod -aG docker vagrant
      sudo systemctl enable docker
      
      sudo yum install -y git
      
      # echo 'export COMPOSE_FILE=docker-compose-development.yml' >> /home/vagrant/.bash_profile
      
      sudo curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
      sudo chmod +x /usr/local/bin/docker-compose
      
      sudo mkdir -p /data/db_data/mysql
      sudo chown -R vagrant:vagrant /data/db_data
  SHELL
end
