
Vagrant.configure("2") do |config|

  config.vm.box = "hashicorp/bionic64"

  config.vm.provider "hyperv" do |hv, override|
    hv.cpus = "6"
    hv.memory = "8192"
    override.vm.network "public_network"
  end

  config.vm.provider "virtualbox" do |vd, override|
    vd.cpus = "4"
    vd.memory = "6144"
    ## For Conan
    override.vm.network "forwarded_port", guest: 7777, host:7777, protocol: "udp"
    override.vm.network "forwarded_port", guest: 7778, host:7778, protocol: "udp"
    override.vm.network "forwarded_port", guest: 27015, host:27015, protocol: "udp"
    ## For Netdata
    override.vm.network "forwarded_port", guest: 19999, host:29999, protocol: "tcp"
  end

  ## might just turn this into a dir once i get some more files
  config.vm.synced_folder "ansible/", "/opt/ansible"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y docker docker-compose
##    cd /opt/ansible/
##    ansible-playbook playbook.yml
  SHELL

end
