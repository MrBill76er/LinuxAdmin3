# Vagrantfile config for Linux Admin 3

$script = <<-SCRIPT
echo Top System usages
ps -eo %mem,%cpu,comm --sort=-%mem | head -n 6
SCRIPT

Vagrant.configure("2") do |config|

# System info
  # config.vm.provision "shell", path: "sysinfo.sh"
  config.vm.provision "shell",
	inline: $script 
     # inline: "ps -eo %mem,%cpu,comm --sort=-%mem | head -n 6"
      

# Run backup on both virtual machines: box1 and box2

  # config.vm.provision "shell", path: "backup_script.sh"

  # config.vm.provision "shell", inline: <<-SHELL

  # sudo apt-get update

  #  SHELL

   config.vm.define "box1" do |box1|

	box1.vm.box="ubuntu/trusty64"

	box1.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"

	box1.vm.network :private_network, ip: "192.168.56.101"

	box1.vm.provider :virtualbox do |v|

	v.customize ["modifyvm", :id, "--memory", 1020]

	
  	end
end
   config.vm.define "box2" do |box2|

	
	#box2.vm.provision "shell", path: "backup_script.sh"
		
		#sudo apt-get install -y nginx

		#SHELL

	box2.vm.box="debian/jessie64"

	box2.vm.network :forwarded_port, guest: 22, host: 10123, id: "ssh"

	box2.vm.network :private_network, ip: "192.168.56.102"
   		
  	end
end

   # config.vm.define "box3Apache" do |box3Apache|

	# box3Apache.vm.box="chrislentz/trusty64-lamp"

	# box3Apache.vm.network :forwarded_port, guest: 22, host: 10124, id: "ssh"

Vagrant.configure("2") do |config|
 

config.vm.define "box4" do |box4|
	box4.vm.box="ubuntu/xenial64"
	box4.vm.network :forwarded_port, guest: 22, host: 10125, id: "ssh"
   end
end	
