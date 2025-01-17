Vagrant.configure("2") do |config|
    # Give a custom name for a VM created by this script for a Vagrant CLI
    config.vm.define "hmlabstk01"
  
    # Name for the box image downloaded from the box_url
    # it will be used to create a folder inside ~/.vagrant.d/boxes to avoid re-downloading
    config.vm.box = "bento/ubuntu-20.04"
  
    # URL used as a source for the vm.box defined above
    config.vm.box_url = "https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-vagrant.box"
  
    # Create additional network interface to make this VM available on the fixed IP address
    # NOTE: I assume that 10.123.123.123 IP is not used in your network
    config.vm.network "public_network", bridge: "enp5s1", ip: "192.168.0.57"
  
    config.vm.provider "virtualbox" do |v|
      # Name visible inside your Virtualbox UI
      v.name = "hmlabstk01"
      # Amount of memory assigned for your VM
      v.memory = 8192 # <--- Adjust this number according to your needs
      # Number of CPUs assigned for your VM
      v.cpus = 4 # <--- Adjust this number according to your needs
  
  
      # Enable nested virtualization, so it will be possible to run VMs inside your VM
      v.customize ["modifyvm", :id, "--nested-hw-virt", "on"]
      # Enable promiscuous mode for the network interface number "2"
      v.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
    end
  
    # Enable provisioning with Ansible
    config.vm.provision "ansible" do |ansible|
      # Name of the file with Ansible Playbook definition
      ansible.playbook = "install-devstack.yml"
    end

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ip-settings.yml"
    end
  end