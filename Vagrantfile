Vagrant.configure("2") do |config|

#Run backup on both virtual machines: box1 and box2

#config.vm.provision "shell", inline: <<-SHELL

#config.vm.provision "shell", path: "backup_script.sh"

config.vm.provision "shell", path: "scriptname.txt"
        
#sudo apt-get update

      #SHELL


	 config.vm.define "box1" do |box1|

         	 box1.vm.box="ubuntu/trusty64"
		 
		 #box1.vm.provision "shell", inline: <<-SHELL
	 	 	#sudo apt-get update
	 		 # SHELL

        	 box1.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"
		 
		 box1.vm.network :private_network, 1p: "192.168.56.101"
		 
		 box1.vm.provider :virtualbox do |v| 
 	         
		 v.customize ["modifyvm", :id, "--memory", 1020]
		
		 end

end

  	config.vm.define "box2" do |box2|

	#box2.vm.provision "shell", path: "backup_script.sh"
		#sudo apt-get install -y nginx

		#SHELL

       	  	box2.vm.box="ubuntu/xenial64" 
         	
		box2.vm.network :forwarded_port, guest: 22, host: 10123, id: "ssh"
		
		box2.vm.network :private_network, 1p: "192.168.56.102"

 	   end

	config.vm.define "box3" do |box3|

	box3.vm.provision "shell", path: "bootstrap.sh"
	
		#sudo apt-get install -y nginx
		#SHELL

       	  	box3.vm.box="hashicorp/bionic64" 
         	
		box3.vm.network :forwarded_port, guest: 22, host: 10124, id: "ssh"
		
		box3.vm.network :private_network, 1p: "192.168.56.105"

 	   end

end
