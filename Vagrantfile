Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.synced_folder ".", "/home/vagrant/dev"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.provision "shell", reboot: true, inline: <<-SHELL
    sudo apt-get update
    sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y
    sudo apt-get autoremove -y
    wget -qO - https://test.docker.com | sudo sh
    sudo usermod -aG docker vagrant
    sudo systemctl enable docker.service
  SHELL
end
