
Vagrant.configure("2") do |config|

  config.vm.box = "hashicorp/bionic64"

  config.vm.network "public_network"

  config.vm.provider "hyperv" do |vb|
    vb.cpus = "6"
    vb.memory = "8192"
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
