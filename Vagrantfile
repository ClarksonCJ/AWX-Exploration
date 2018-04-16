memory = 2048
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.hostmanager.manage_host = true

  config.vm.define "devtest" do |target|
    target.vm.box = "bento/centos-7.4"
    target.vm.hostname = "devtest"

    # Allocating a static IP here causes Vagrant to hang when reloading the box
    # Since we have no need for a static IP we allocate it dynamically, which
    # solves the problem
    target.vm.network :private_network, type: "dhcp"
  end

  # To avoid Authentication failure on Mac
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", memory]
    vb.customize ["modifyvm", :id, "--cpus", 2]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  config.vm.box_check_update = false
  
end
