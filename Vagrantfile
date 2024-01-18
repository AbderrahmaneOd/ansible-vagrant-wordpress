Vagrant.configure("2") do |config|
  
    config.vm.define "ansible-controller" do |controller|
      controller.vm.hostname = "controller"
      
      controller.vm.box = "centos/7"
      
      controller.vm.provision "shell", inline: <<-SHELL
        sudo yum install epel-release -y
        sudo yum install ansible -y
      SHELL
      
      controller.vm.provision "file", source: "./ansible", destination: "~/ansible"
    end
  
    config.vm.define "web" do |web|
      web.vm.box = "centos/7"
      web.vm.hostname = "web"
      web.vm.network "private_network", ip: "192.168.33.10"
      
      web.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
      web.vm.usable_port_range = (8000..9000)
    end
  
    config.vm.define "db" do |db|
      db.vm.box = "centos/7"
      db.vm.hostname = "db"
      db.vm.network "private_network", ip: "192.168.33.11"
    end
    
  end
  