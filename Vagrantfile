Vagrant.configure("2") do |config|
  config.vm.box = "centos5.8"
  config.vm.box_url = "http://tag1consulting.com/files/centos-5.8-x86-64-minimal.box"

  config.vm.provider "virtualbox" do |vb|
  end
  

  config.vm.network :private_network, :ip=>"33.33.33.33", :drop_nat_interface_default_route=>true
  #config.vm.network :public_network, :bridge => "wlan0"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true
  config.berkshelf.berksfile_path = "./Berksfile"
  
  config.vm.provision :chef_solo do |chef|
    chef.run_list = ["recipe[wordpress]"]
    chef.json = {
      "apache" => {
        "default_site_enabled" => false,
        "allow_override" => "all" 
      },
      "wordpress" => {
        "dir" => "/var/www/wordpress",
        "db" => {
          "name"=> "my_wordpress_db", 
          "host"=> "localhost",
          "user"=> "admin",
          "pass"=> "admin"
        }
      }
    }
    #chef.json = {
    #  "apache" => {
    #    "server_name" =>"www.example.vm",
    #    "server_aliases" => "example.vm",
    #    "allow_override" => "all",        
    #    "listen_address" => "10.0.2.15",
    #    "ssl_verify_mode" => :verify_peer,
    #    "default_site_enabled" => true,
    #    "docroot_dir" => "/var/www/html"
    #  }
  	#}
  end
end
