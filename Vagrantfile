VAGRANTFILE_API_VERSION = "2"
   Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
      config.vm.box = "ubuntu/trusty64"
      config.vm.network "forwarded_port", guest: 80, host: 8080
      config.vm.network "forwarded_port", guest: 21, host: 2121

      config.vm.provider "virtualbox" do |v|
         v.memory = 4096
      end

      config.vm.provision "ansible" do |ansible|
         ansible.extra_vars = {
            ntp_server: "pool.ntp.org",
            ansible_ssh_user: 'vagrant' 
         }
         ansible.verbose = 'vvvv'
         ansible.playbook = "galaxy.yml"
      end
   end
