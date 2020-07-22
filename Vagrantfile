# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian10"
  config.vm.network "forwarded_port", guest: 3000, host: 3000, host_ip: "127.0.0.1", auto_correct: true
  config.vm.synced_folder "./", "/opt/app", SharedFoldersEnableSymlinksCreate: false
  config.ssh.extra_args = ["-t", "cd /opt/app; bash --login"]

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo apt-get install -y ruby-full build-essential libpq-dev imagemagick graphviz zlibc zlib1g zlib1g-dev postgresql
    sudo -u postgres psql postgres -c "ALTER ROLE postgres WITH PASSWORD 'password';"  
    sudo systemctl enable postgresql  
    cd /opt/app
    sudo gem install bundler
    bundle install
  SHELL

  config.vm.provision "shell", privileged: false, run: "always", inline: <<-SHELL
    cd /opt/app
    cp -n env.sample .env
    bundle exec rails s -d -b 0.0.0.0
  SHELL
end
