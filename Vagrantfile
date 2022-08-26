# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  number_of_machines = 3
  box_name = "generic/ubuntu2004"

  base_ip = 100
  base_ip_addresses = "192.168.51"

  ip_addresses = (1..number_of_machines).map{ |i| "#{base_ip_addresses}.#{base_ip + i}" }

  script = <<-SCRIPT
    echo "hello world"
  SCRIPT

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  (1..number_of_machines).each do |i|
    config.vm.define "box_#{i}" do |box|
      box.vm.box = box_name
      box.vm.network "private_network", ip: "#{ip_addresses[i-1]}"

      box.vm.provision "shell", inline: "#{script}"
    end
  end
end
