Vagrant.configure('2') do |config|
  VM_MEMORY = 6*1024
  VM_CORES = 4

  config.vm.hostname='bosh-lite'
  config.vm.box = 'boshlite-ubuntu1204-build55'
  config.vm.network :private_network, ip: '192.168.50.4'

  config.vm.provider :virtualbox do |v, override|
    override.vm.box_url = 'http://bosh-lite-build-artifacts.s3.amazonaws.com/55/boshlite-virtualbox-ubuntu1204.box'
    v.customize ["modifyvm", :id, "--memory", VM_MEMORY]
    v.customize ["modifyvm", :id, "--cpus", VM_CORES]
  end

  config.vm.provider :vmware_fusion do |v, override|
    override.vm.box_url = 'http://bosh-lite-build-artifacts.s3.amazonaws.com/55/boshlite-vmware-ubuntu1204.box'
    v.vmx["numvcpus"] = VM_CORES
    v.vmx["memsize"] = VM_MEMORY
  end

end
