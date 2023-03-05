# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile
# For building k8s node

nodes = [
  {
    :hostname => "master",
    :eth1 => "192.168.56.1",
    :mem  => "4096",
    :cpu => "2"
  },
  {
    :hostname => "node1",
    :eth1 => "192.168.56.2",
    :mem  => "2048",
    :cpu  => "2"
  },
  {
    :hostname => "node2",
    :eth1 => "192.168.56.3",
    :mem  => "2048",
    :cpu  => "2"
  }
]

Vagrant.configure(2) do |config|
  # https://app.vagrantup.com/ubuntu/boxes/focal64
  config.vm.box = "ubuntu/focal64"
	
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.hostname = node[:hostname]
      
      nodeconfig.vm.provider "virtualbox" do |vb|
        vb.customize [
          "modifyvm", :id,
          "--memory", node[:mem]
        ]
        vb.customize [
          "modifyvm", :id,
          "--cpus", node[:cpu]
        ]
      end
      config.vm.network :private_network, ip: node[:eth1]
    end
  end
  config.vm.provision :shell, path: "./build_k8s_tool.sh"
end
