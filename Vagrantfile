Vagrant.configure("2") do |config|
	config.vm.box = "ubuntu/xenial64"

	config.vm.hostname = "ansiblets3"
	config.vm.network "public_network"

	config.vm.provider "virtualbox" do |v|
		v.name = "ansiblets3"
		v.memory = 2048
		v.cpus = 2
		v.linked_clone = true
		v.gui = false
	end

	config.vm.provision "shell" do |s|
		s.inline = "apt-get update && apt-get upgrade -y && apt-get install -y python"
	end

	config.vm.provision "ansible" do |a|
		a.verbose = "v"
		a.playbook = "provision/playbook.yml"
	end
end