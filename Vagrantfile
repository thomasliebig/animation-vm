# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.ssh.insert_key = true
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     vb.memory = "8192"
  end
  
  config.vm.provision "shell", privileged:false, inline: <<-SHELL
    passwd -d -u ubuntu
    chage -d0 ubuntu

    sudo echo "LANG=en_US.UTF-8" >> /etc/environment
    sudo echo "LANGUAGE=en_US.UTF-8" >> /etc/environment
    sudo echo "LC_ALL=en_US.UTF-8" >> /etc/environment
    sudo echo "LC_CTYPE=en_US.UTF-8" >> /etc/environment
    sudo add-apt-repository -y ppa:webupd8team/java
    sudo apt-get update
    sudo apt-get -y upgrade
    echo debconf shared/accepted-oracle-license-v1-1 select true | sudo debconf-set-selections 
    echo debconf shared/accepted-oracle-license-v1-1 seen true | sudo debconf-set-selections
    sudo apt-get -y install oracle-java8-installer
    
    sudo apt-get install -y xfce4 virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
    sudo apt-get install gnome-icon-theme-full tango-icon-theme
    sudo echo "allowed_users=anybody" > /etc/X11/Xwrapper.config
  
    sudo apt-get install -y apache2 libapache2-mod-php5
    sudo a2enmod rewrite

    sudo rm /var/www/html/*
     rmdir /var/www/html
    sudo ln -s /vagrant/dokuwiki/dokuwiki /var/www/html
    sudo chown -R www-data:www-data /var/www/html
    sudo chown -R www-data:www-data /vagrant/dokuwiki/dokuwiki

    sudo service apache2 restart

    sudo apt-get install -y sqlite3 libsqlite3-dev
    sudo add-apt-repository -y ppa:fkrull/deadsnakes
    sudo apt-get update
    sudo apt-get install -y python3
    sudo apt-get install -y python3-pip
    

    # nodejs test client configuration
    sudo apt-get install -y nodejs-legacy
    sudo apt-get install -y npm
    sudo apt-get install -y git

    # Synfig
    sudo apt-get install -y synfigstudio
    sudo apt-get install -y synfig
    

    # Renderchan dependencies: sox, zip, ffmpeg
    # flac, krita, mpg123, vorbis, pencil2d
    sudo apt-get install -y sox
    sudo apt-get install -y zip
    sudo add-apt-repository -y ppa:mc3man/trusty-media
    sudo apt-get update
    sudo apt-get install -y ffmpeg
    sudo apt-get install -y flac
    sudo apt-get install -y krita
    sudo apt-get install -y mpg123
    sudo apt-get install -y vorbis-tools
    sudo apt-get install -y pencil2d

    sudo apt-get -f install -y
    sudo apt-get install -y qt5-default qttools5-dev-tools qtmultimedia5-dev libqt5svg5-dev libqt5xmlpatterns5-dev libpulse-dev
    sudo apt-get install -y qtcreator
    sudo apt-get install make clang

    cd /vagrant
    wget http://download.tuxfamily.org/morevna/packages/pencil/pencil2d_0.5.4-20130728.1_amd64.deb
    sudo dpkg -i *.deb

    # Blender
    sudo add-apt-repository -y ppa:irie/blender
    sudo apt-get update
    sudo apt-get install -y blender


    # Renderchan
    git clone https://github.com/morevnaproject/RenderChan.git /home/vagrant/renderchan
    echo "export PATH=\"\$HOME/renderchan/bin/:\$PATH\"" >> /home/vagrant/.bashrc

    # Inkscape
    sudo apt-get install -y inkscape

    # Gimp
    sudo apt-get install -y gimp


    # Natron
    sudo apt-get install -y libegl1-mesa
    cd /vagrant
    wget https://netcologne.dl.sourceforge.net/project/natron/Linux/64/releases/Natron-2.3.1-Linux-x86_64bit-portable.tar.xz
    mkdir /home/vagrant/Natron
    tar xf /vagrant/Natron-2.3.1-Linux-x86_64bit-portable.tar.xz -C /home/vagrant/Natron

    mkdir /home/vagrant/Desktop
    cp  /vagrant/xfce-settings/Desktop/* /home/vagrant/Desktop/
    sudo startxfce4&

  SHELL

  config.vm.network :forwarded_port, guest: 80, host: 8800
  config.vm.network :forwarded_port, guest: 8080, host: 8080
 
end

