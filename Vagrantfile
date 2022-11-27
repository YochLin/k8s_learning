# Vagrantfile
# For building k8s node

nodes = [
  {
	:hostname => "master",
	:eth1 => "192.168.40.1",
	:mem  => "4096",
	:cpu" => "2"
  },
  {
	:hostname => "node1",
	:eth1 => "192.168.40.2",
	:mem  => "2048",
	:cpu  => "2"
  },
  {
	:hostname => "node2",
	:eth1 => "192.168.40.3",
	:mem  => "2048",
	:cpu  => "2"
  }
]

Vagrant.configure(2) do |config|
  # https://app.vagrantup.com/ubuntu/boxes/focal64
  config.vm.box = "ubuntu/focal64"
	
  nodes.each do |node|
	config.vm.define node[:name] do |nodeconfig|
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
  end
end
  # config.vm.provision :shell, path: "setup.sh"
end
