# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "harvardcatalyst/centos-6-rails"

  # sync folders, please configure this
  config.vm.synced_folder "..", "/vagrant", type: "rsync",
      rsync__exclude: ".git/"

  config.vm.network "forwarded_port", guest: 9000, host: 9000

  # enable this to use ssh agent on host machine
  config.ssh.forward_agent = true

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    ssh-keyscan -H github.com >> ~/.ssh/known_hosts

    pip install -q awscli

    # Nokogiri 1.4.7 requires this
    sudo yum -y install libxslt-devel

    # /home/vagrant/.rbenv/bin/rbenv install 2.1.3
    #/home/vagrant/.rbenv/shims/gem install bundler
    #echo 'ln -s /vagrant/true-sql/true-sql /usr/local/bin/true-sql' >> ~/.bash_profile
    #echo 'source "/vagrant/true-sql/completion.bash"' >> ~/.bash_profile
  SHELL
end
