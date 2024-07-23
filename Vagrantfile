Vagrant.configure("2") do |config|
  config.vm.box = "gusztavvargadr/visual-studio-2022-community-windows-10"
  config.vm.box_version = "2202.0.2404"
  
  config.vm.define "inWinsible"
  config.vm.network "private_network", ip: "192.168.56.50"

  config.vm.guest = :windows
  config.vm.communicator = "winrm"

  config.vm.provision :shell, :path => "provision/Install-WMF3Hotfix.ps1", privileged: false
  config.vm.provision :shell, :path => "provision/ConfigureRemotingForAnsible.ps1", privileged: false

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "inventory"
    ansible.playbook = "main.yml"
    ansible.host_key_checking = false
    # ansible.verbose = "vvv"
  end
end
