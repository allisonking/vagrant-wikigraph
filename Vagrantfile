# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # More boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 8000, host: 8001

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
