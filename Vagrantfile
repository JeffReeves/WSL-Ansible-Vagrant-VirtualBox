
Vagrant.configure(2) do |config|

    # install Ubuntu 14.04 LTS
    config.vm.box = "ubuntu/trusty64"

    # access port 80 of the VM on port 8080 of the host
    config.vm.network "forwarded_port", guest: 80, host: 8080

    # --[ ONLY UNCOMMENT ONE OF THE OPTIONS BELOW ]-----

    # OPTION 1: use Ansible on WSL
    config.ssh.insert_key = false
    config.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook.yml"
    end

    # OPTION 2: Have Ansible run on the VM itself once it's made
    #config.vm.provision "ansible_local" do |ansible|
    #    ansible.playbook = "playbook.yml"
    #end
end
