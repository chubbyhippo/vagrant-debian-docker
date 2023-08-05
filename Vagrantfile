Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian11"
  config.vm.synced_folder ".", "/home/vagrant/dev"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.provision "shell", reboot: true, inline: <<-SHELL
    sudo apt update
    sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
    sudo apt autoremove -y
    curl -fsSL https://test.docker.com | sudo sh
    sudo usermod -aG docker vagrant
    sudo systemctl enable docker.service
  SHELL
end
