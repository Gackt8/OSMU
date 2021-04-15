
Vagrant.configure("2") do |config|
  
  
  servers=[
	{
	:hostname => "m1",
	:box => "ubuntu/xenial64",
	:ip => "172.16.1.54",
	:ssh_port => '2220'
	},
	{
	:hostname => "m2",
	:box => "ubuntu/xenial64",
	:ip => "172.16.1.55",
	:ssh_port => '2221'
	},
	{
	:hostname => "m3",
	:box => "ubuntu/xenial64",
	:ip => "172.16.1.56",
	:ssh_port => '2223'
	}
  ]
  
  
  servers.each do |machine|
		config.vm.define machine[:hostname] do |node|
			node.vm.box = machine[:box]
			node.vm.hostname = machine[:hostname]
			node.vm.network :private_network, ip: machine[:ip]
			node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
			node.vm.synced_folder "d:/Projects/OSMU/VirtualBox", "/var/www"

			
			#node.vm.provision "shell", 
			#inline: "
			#sudo apt-get update
			#sudo apt-get install git
			#git init .
			#git remote add -f origin https://github.com/Gackt8/OSMU
			#git checkout Task3
			#git show :task3_1.txt
			#git remote
			
			#обновление локального репозитория
			#git remote update myorigin --prune
			#git pull
			
			#SSH
			#ssh-keygen -b 4096
			#ssh-copy-id username@remote_host
			#ssh username@remote_host

			
			node.vm.provision "shell", 
				
			inline: '
			
			ssh-keygen -b 4096
			ssh-copy-id username@remote_host
			ssh username@remote_host
			
			',
			run: "always",
			privileged: "false"

				
			node.vm.provider :virtualbox do |vb|
				vb.gui = false
				vb.memory = 1024
				vb.cpus = 2
				
			end
				
		end
	
	end
	
end
