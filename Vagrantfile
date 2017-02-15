VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.ssh.insert_key = false
    config.vm.box_check_update = false

    config.vm.define "vagrant1" do |vagrant1|
        vagrant1.vm.box = "bento/centos-7.1"
        vagrant1.vm.network "private_network", ip: "192.168.168.201"

        # On CentOS7, you should restart network to take effect of ip address; but you need not to do this on ubuntu-16.10

        # set preserve_order to true in order to execute as I wish.
        vagrant1.vm.provision "restart-network", type: "shell", preserve_order: true, inline: "sudo systemctl restart network"

        # install repo to test
        vagrant1.vm.provision "install epel repo", type: "shell", preserve_order: true, inline: "sudo yum -y install epel-release"


        vagrant1.vm.provision "ansible" do |ansible|
            preserve_order = true
            ansible.limit = "all"
            ansible.verbose = "v" # "v" or "vvvv"
            ansible.playbook = "tests/test_vagrant.yml"

            ansible.groups = {
                "rabbitmq" => ["vagrant1"]
            }
        end

    end
end
