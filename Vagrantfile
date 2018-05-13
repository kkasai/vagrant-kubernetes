Vagrant.configure("2") do |config|
  config.vm.define "k8s-master" do |node|
    node.vm.box = "bento/centos-7.4"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    node.vm.network "private_network", ip: "192.168.33.11"
    node.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.verbose = "-vvv"
      ansible.inventory_path = "ansible/inventory"
      ansible.extra_vars = {
        hostname: "k8s-master"
      }
    end
  end
  config.vm.define "worker-node1" do |node|
    node.vm.box = "bento/centos-7.4"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    node.vm.network "private_network", ip: "192.168.33.12"
    node.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.verbose = "-vvv"
      ansible.inventory_path = "ansible/inventory"
      ansible.extra_vars = {
        hostname: "worker-node1"
      }
    end
  end
end
