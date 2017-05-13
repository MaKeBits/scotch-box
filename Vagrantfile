# -*- mode: ruby -*-
# vi: set ft=ruby :

#Start using yaml for config
#require 'yaml'
#settings = YAML.load_file 'vagrant.yaml'

### set default vars
# Store the current version of Vagrant for use in conditionals when dealing
# with possible backward compatible issues.
vagrant_version = Vagrant::VERSION.sub(/^v/, '')
# directory name of box
box_pwd = Dir.pwd
vagrant_dir = File.expand_path(File.dirname(__FILE__))

Vagrant.configure("2") do |config|

    config.vm.box = "scotch/box"
    config.vm.define "scotchbox"
    config.vm.network "private_network", ip: "192.168.33.10"
    config.vm.hostname = "scotchbox"

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = "1"
      vb.natdnsproxy1 = "on"
      vb.natdnshostresolver1 = "on"
      vb.name = File.basename(box_pwd)
    end


    config.vm.synced_folder ".", "/var/www", :mount_options => ["dmode=777", "fmode=666"]

    # Optional NFS. Make sure to remove other synced_folder line too
    #config.vm.synced_folder ".", "/var/www", :nfs => { :mount_options => ["dmode=777","fmode=666"] }

end
