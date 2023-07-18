# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    config.ssh.insert_key = false

    config.vm.synced_folder ".", "/vagrant", disabled: true

    config.vm.provider :libvirt do |v|
      # v.memory = 256
      # v.linked_clone = true
    end

    config.vm.define "server" do |guest|
        guest.vm.provider "libvirt" do |vm|
            vm.memory = 1024
            vm.cpus = 1
        end

        guest.vm.box = "generic/alma8"
        guest.vm.hostname = "server"
        guest.vm.network "private_network", ip: "192.168.123.10"
    end


    config.vm.define "logstash" do |guest|
      guest.vm.provider "libvirt" do |vm|
          vm.memory = 1024
          vm.cpus = 1
      end

      guest.vm.box = "generic/alma9"
      guest.vm.hostname = "logstash"
      guest.vm.network "private_network", ip: "192.168.123.20"
  end
  end
