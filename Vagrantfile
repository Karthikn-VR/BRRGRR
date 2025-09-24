Vagrant.configure("2") do |config|
  # Use Ubuntu 22.04
  config.vm.box = "ubuntu/jammy64"

  # Private network IP for easy access
  config.vm.network "private_network", ip: "192.168.56.10"

  # Forward guest port 80 to host port 1234
  config.vm.network "forwarded_port", guest: 80, host: 1234

  # Allocate more RAM and CPU for Docker
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  # Automatically install Docker
  config.vm.provision "docker"

  # Optional: Run Ansible playbook inside VM
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/install_nginx.yml"
  end
end
# Vagrantfile for setting up a VM with Docker and Nginx