# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION="2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # add for dns
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  config.vm.box = "CentOS6.4"
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/515908/CentOS-6.4-x86.box"

  config.vm.provision :shell, inline: <<-EOF
    sudo rpm -i \
    http://yum.puppetlabs.com/puppetlabs-release-el-6.noarch.rpm
    sudo yum install -y puppet
  EOF


  config.vm.define :app do |c|
    c.vm.provision :shell do |shell|
      shell.path = "provision.sh"
      shell.args = "app"
    end
  end
end
