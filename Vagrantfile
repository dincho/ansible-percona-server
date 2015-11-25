VAGRANTFILE_API_VERSION = "2"
ROLE_NAME = File.basename(File.expand_path(File.dirname(__FILE__)))

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "test", primary: true do |node|
    node.vm.box = "ubuntu/trusty32"

    node.vm.provider "virtualbox" do |vb|
      vb.name = ROLE_NAME
      vb.customize ["modifyvm", :id, "--memory", "256"]
    end
    
    node.vm.provider "parallels" do |vm, override|
      override.vm.box = "parallels/ubuntu-14.04-i386"
      vm.name = ROLE_NAME
      vm.customize ["set", :id, "--memsize", "256"]
    end

    node.vm.provision "ansible" do |ansible|
        ansible.sudo = true
        ansible.playbook = "tests/play.yml"
        ansible.verbose = "vv"
    end
  end
end
