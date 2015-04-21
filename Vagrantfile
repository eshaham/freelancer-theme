$script = <<SCRIPT

sudo apt-get -y update
sudo apt-get -y install curl
sudo apt-get -y install build-essential

# git
sudo apt-get -y install git-core

# node
curl -sL https://deb.nodesource.com/setup | sudo bash -
sudo apt-get -y install nodejs

# ruby
sudo apt-get -y install ruby1.9.3

# npm modules
sudo npm install -g grunt-cli
sudo npm install -g bower
npm install

#gems
sudo gem install github-pages --no-ri --no-rdoc
sudo gem install thor --no-ri --no-rdoc
sudo gem install stringex --no-ri --no-rdoc

# bower
bower install

# cleanup
sudo apt-get clean

SCRIPT

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 4000, host: 4000, auto_correct: true

  config.vm.provider "virtualbox" do |v|
      v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
    end

  config.vm.provision "shell", inline: $script

  config.ssh.forward_agent = true
end