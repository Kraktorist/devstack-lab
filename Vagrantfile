Vagrant.configure("2") do |config|
    config.vm.define 'hmlabstk01' do |config|
      config.vm.provider "virtualbox" do |vb|
        vb.cpus = "2"
        vb.memory = "8192"
      end
      config.vm.box = "bento/ubuntu-20.04"
      config.vm.hostname = 'hmlabstk01'
      config.vm.network "public_network", ip: "192.168.0.57"
    end

    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--nested-hw-virt", "on"]
        # you need this for openstack guests to talk to each other
        vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]

      end
end