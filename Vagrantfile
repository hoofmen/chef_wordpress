# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "andres-centos-6.5"
  config.vm.box_url = "./Centos6.5.box"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
   
  config.vm.provider "virtualbox" do |vb|
  
  end
  
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.omnibus.chef_version = :latest
  config.berkshelf.berksfile_path = "./Berksfile"
  config.vm.provision :chef_solo do |chef|
  	chef.run_list = ["recipe[apache2]"]
  	chef.json = {
  		"wordpress"=>{ 
  			"db"=>{ 
  				"name"=> "my_wordpress_db", 
	  			"host"=> "localhost",
	  			"user"=> "admin",
	  			"pass"=> "admin"
	  		}
	  	}
  	}

  end
end
