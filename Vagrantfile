# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define :owasp do |owasp|
    owasp.vm.box = "ubuntu/bionic64"
    owasp.vm.hostname = "owasp"
    owasp.vm.provider "virtualbox" do |vbox|
      vbox.name = "owasp"
      vbox.memory = 2048
      vbox.cpus = 2
    end
    owasp.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/owasp.yml"
      ansible.galaxy_roles_path = "ansisble/roles/"
      ansible.extra_vars = {
        ansible_python_interpreter:"/usr/bin/python3",
        host_name:"owasp.my.local"
     }
    end
    owasp.vm.network "private_network", :ip => "192.168.56.20", :name => "vboxnet0", :adapter => 2
  end

end
