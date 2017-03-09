# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "bento/ubuntu-16.04"

  #config.vm.network "forwarded_port", guest: 80, host: 8000  # Use guest's NGINX proxy
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.synced_folder "~/workspaces/ftf-geonode/ftf_geonode.git", "/home/vagrant/ftf_geonode.git"
  config.vm.synced_folder "~/workspaces/public/geonode.git", "/home/vagrant/geonode.git"

  config.vm.provider "virtualbox" do |vb|\
      vb.gui = false
      vb.cpus = 2
      vb.memory = 4096
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/ftf_geonode.yml"
    ansible.host_key_checking = false
    ansible.verbose = "v"
    ansible.raw_arguments = []
  end

end
