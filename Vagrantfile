$script = <<-SCRIPT
apt-get update
apt-get install git docker docker-compose -y
git clone https://github.com/davideagle/htpc-download-box.git
mkdir /media
chown -R vagrant:vagrant /media
systemctl enable docker && systemctl start docker
chown -R vagrant:vagrant htpc-download-box
cd htpc-download-box
docker-compose up -d
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provision "shell", inline: $script
  config.vm.network "private_network", type: "dhcp"
end
