Vagrant.configure("2") do |config|
  config.vm.box = "stereohorse/alfa-infra-sandbox"

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  config.vm.define 'vm1' do |node|
    node.vm.hostname = 'vm1'
    node.vm.network :private_network, ip: '192.168.5.2'

    node.vm.provider "virtualbox" do |v|
      v.memory = 1536
      v.cpus = 1
    end
  end

  config.vm.define 'vm2' do |node|
    node.vm.hostname = 'vm2'
    node.vm.network :private_network, ip: '192.168.5.3'

    node.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "play-site.yml"
    ansible.compatibility_mode = "2.0"
    ansible.groups = {
      "masters" => ["vm1"],
      "agents" => ["vm1", "vm2"]
    }
  end
end
