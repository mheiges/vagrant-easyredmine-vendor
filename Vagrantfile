#IP='192.168.100.151'
Vagrant.configure(2) do |config|

  config.ssh.username  = 'easy'
  config.ssh.forward_agent = 'true'

  config.vm.provider "virtualbox" do |v|
    v.gui = true
  end

  config.vm.box = "ebrc/easyredmine-20151110-vendor"
  config.vm.box_url = 'http://software.apidb.org/vagrant/easyredmine-20151110-vendor.json'

  config.vm.hostname = 'easyredmine.vm.apidb.org'
  #config.vm.network :private_network, ip: IP
  config.vm.network "private_network", type: "dhcp"



  if Vagrant.has_plugin?('landrush')
    config.landrush.enabled = true
    config.landrush.tld = 'vm.apidb.org'
    #config.landrush.host 'easyredmine.vm.apidb.org', IP
    #config.landrush.host_ip_address = IP
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = 'playbook.yml'
  end

end
