Vagrant.configure("2") do |config|

  ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

  net_ip = "192.168.51"

  [
    ["controller", "#{net_ip}.10", "2048", "centos/8"],
    ["compute", "#{net_ip}.11", "2048", "centos/8"],
  ].each do |vmname,ip,mem,os|
    config.vm.define "#{vmname}" do |vm_config|
      vm_config.vm.provider "virtualbox" do |vb|
          vb.memory = "#{mem}"
          vb.cpus = 2
          vb.name = "#{vmname}"
      end
      vm_config.vm.provider "libvirt" do |libvirt|
          libvirt.memory = "#{mem}"
          libvirt.cpus = 2
      end
      vm_config.vm.box = "#{os}"
      vm_config.vm.hostname = "#{vmname}"
      vm_config.vm.network "private_network", ip: "#{ip}"
    end
  end
end
