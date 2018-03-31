# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 8000, host: 8001

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "shared-folder/", "/vagrant_data"
  config.vm.synced_folder "playbooks/", "/ansible", mount_options: ["ro"]

  # Enable provisioning with Ansible
  config.vm.provision "ansible_local" do |ansible|
    provisioning_path = "/ansible"
    ansible.playbook = "/ansible/install.yml"
    ansible.compatibility_mode = "2.0"
    ansible.verbose = false
  end
end
