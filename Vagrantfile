Vagrant.configure("2") do |config|
  config.vm.define "node" do |node|
    node.vm.box = "centos/7"
    node.vm.hostname ="node"
    node.vm.box_url = "centos/7"
      node.vm.base_mac = "525400261060"

      node.vm.network "private_network", ip: "192.168.33.10"
      node.vm.network "forwarded_port", guest: 443, host: 443, auto_correct:true
      node.vm.network "forwarded_port", guest: 22, host: 22, auto_correct:true
      node.vm.network "forwarded_port", guest: 80, host: 80, auto_correct:true


      node.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--memory", 512]
          v.customize ["modifyvm", :id, "--name", "node"]
        end
    end

    config.vm.define "node2" do |node2|
      node2.vm.box = "centos/7"
      node2.vm.hostname ="node2"
      node2.vm.box_url = "centos/7"
      node2.vm.base_mac = "525400261061"

      node2.vm.network "private_network", ip: "192.168.33.11"
      node2.vm.network "forwarded_port", guest: 80, host: 80, auto_correct:true
      node2.vm.network "forwarded_port", guest: 22, host: 22, auto_correct:true
      node2.vm.network "forwarded_port", guest: 443, host: 443, auto_correct:true

      node2.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--memory", 512]
          v.customize ["modifyvm", :id, "--name", "node2"]
        end
    end
    config.vm.define "node3" do |node3|
      node3.vm.box = "centos/7"
      node3.vm.hostname ="node3"
      node3.vm.box_url = "centos/7"
      node3.vm.base_mac = "525400261061"

      node3.vm.network "private_network", ip: "192.168.33.13"
      node3.vm.network "forwarded_port", guest: 80, host: 80, auto_correct:true
      node3.vm.network "forwarded_port", guest: 22, host: 22, auto_correct:true
      node3.vm.network "forwarded_port", guest: 443, host: 443, auto_correct:true

      node3.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--memory", 512]
          v.customize ["modifyvm", :id, "--name", "node3"]
        end
    end
    config.vm.define "node4" do |node4|
      node4.vm.box = "centos/7"
      node4.vm.hostname ="node4"
      node4.vm.box_url = "centos/7"
        node4.vm.base_mac = "525400261060"

        node4.vm.network "private_network", ip: "192.168.33.12"
        node4.vm.network "forwarded_port", guest: 443, host: 443, auto_correct:true
        node4.vm.network "forwarded_port", guest: 22, host: 22, auto_correct:true
        node4.vm.network "forwarded_port", guest: 80, host: 80, auto_correct:true

        node4.vm.provider :virtualbox do |v|
          v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
          v.customize ["modifyvm", :id, "--memory", 512]
            v.customize ["modifyvm", :id, "--name", "node4"]
          end
      end
end
