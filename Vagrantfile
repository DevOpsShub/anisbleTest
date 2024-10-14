Vagrant.configure("2") do |config|
  # Developer Workstation Configuration
  config.vm.define "dev_workstation" do |dev|
    dev.vm.box = "ubuntu/bookworm64"
    dev.vm.hostname = "dev_workstation"
    dev.vm.network "private_network", type: "dhcp"
    dev.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2
    end
    dev.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.groups = {
        "developer_workstation" => ["dev_workstation"],
      }
    end
  end

  # Jenkins Master Configuration
  config.vm.define "jenkins_master" do |jenkins|
    jenkins.vm.box = "ubuntu/bookworm64"
    jenkins.vm.hostname = "jenkins_master"
    jenkins.vm.network "private_network", type: "dhcp"
    jenkins.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2
    end
    jenkins.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.groups = {
        "jenkins_master" => ["jenkins_master"],
      }
    end
  end
end
