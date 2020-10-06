# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.box_check_update = true

  config.vm.provider "vmware_desktop" do |v|
  v.vmx["memsize"] = "4096"
  v.vmx["numvcpus"] = "2"
  v.gui = true
end
  config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get dist-upgrade -y
     sudo apt install open-vm-tools-desktop open-vm-tools
     sudo apt-get install -y apache2 firefox chromioum
     sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
     sudo apt install -y --no-install-recommends ubuntu-desktop
     sudo apt install --assume-yes chromium-browser
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
     sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt update
     sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose unzip
     sudo systemctl enable docker
     sudo apt install -y --no-install-recommends ubuntu-desktop
     sudo wget https://github.com/SecurityRiskAdvisors/VECTR/releases/download/ce-5.7.0/sra-vectr-runtime-5.7.0-ce.zip
     unzip sra-vectr-runtime-5.7.0-ce.zip
     sed -i 's/sravectr.internal/vectr.internal/g' .env
     echo "127.0.0.1 vectr.internal" >> /etc/hosts 
   SHELL
end