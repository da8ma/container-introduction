# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.provider "vmware_desktop" do |v|
    v.vmx["memsize"] = "1024"
    v.vmx["numvcpus"] = "2"
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update

    apt-get install apt-transport-https ca-certificates curl software-properties-common jq -y
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt-get update
    apt-get install -y docker-ce

    apt-get install -y cgdb
    apt-get install -y cgroup-tools

    apt-get install -y make gcc
    git clone git://git.kernel.org/pub/scm/linux/kernel/git/morgan/libcap.git /usr/src/libcap
    (cd /usr/src/libcap && make && make install)
  SHELL
end