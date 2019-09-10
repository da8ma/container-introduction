# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "swallat/ubuntu-18.04-parallels"
  config.vm.box_version = "1.0"
  config.vm.provider "parallels" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt update

    apt install apt-transport-https ca-certificates curl software-properties-common jq -y
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt update
    apt install -y docker-ce

    apt install -y cgdb
    apt install -y cgroup-tools

    apt install -y gcc
    git clone git://git.kernel.org/pub/scm/linux/kernel/git/morgan/libcap.git /usr/src/libcap
    (cd /usr/src/libcap && make && make install)
  SHELL
end