
Vagrant.configure(2) do |config|

    # install Ubuntu 14.04 LTS
    config.vm.box = "ubuntu/trusty64"

    # access port 80 of the VM on port 8080 of the host
    config.vm.network "forwarded_port", guest: 80, host: 8080

    # --[ ONLY UNCOMMENT ONE OF THE OPTIONS BELOW ]-----

    # OPTION 1: use Ansible on WSL
    #config.ssh.insert_key = false
    #config.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
    #config.vm.provision "ansible" do |ansible|
    #    ansible.playbook = "playbook.yml"
    #end

    # OPTION 2: Have Ansible run on the VM itself once it's made
    #config.vm.provision "ansible_local" do |ansible|
    #    ansible.playbook = "playbook.yml"
    #end

    # OPTION 3: Run Ansible from a remote machine
    config.vm.network "forwarded_port", id: "ssh", guest: 22, host: 2222
    # NOTE: Before running Ansible, complete the following on the 
    #   remote machine:
    #
    #   - Copy the playbook.yml, index.html, and vhost.tpl:
    #       scp playbook.yml index.html vhost.tpl <user>@<host>:<location>
    #
    #   - Copy the private key used for the vagrant user:
    #       KEY=$(vagrant ssh-config | grep IdentityFile | awk '{print $2}')
    #       scp "${KEY}" <user>@<host>:<location>
    #
    #   - Create a host inventory file:
    #       ssh <user>@<host>
    #       sudo vim /etc/ansible/hosts
    #       # insert the following:
    #           <hostname> ansible_host=<ip-address> ansible_port=2222 ansible_user=vagrant ansible_private_key_file=<key-copied-from-earlier>
    #
    #   - Verify you can ping:
    #       ansible all -m ping
    #           # <hostname> | SUCCESS => {
    #           #     "changed": false, 
    #           #     "ping": "pong"
    #           # }
    #
    #   - Run the Ansible Playbook:
    #       cd <location-of-playbook>
    #       ansible-playbook playbook.yml
    #
    #   NOTE: If you destroy and rebuild the vagrant box you will want to
    #       remove the old entry in the remote machine's ~/.ssh/known_hosts
    #       file, otherwise you will get an error when trying to ping or 
    #       run the playbook.
end
