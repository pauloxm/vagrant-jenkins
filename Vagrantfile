
Vagrant.configure("2") do |config|
  config.vm.define :jenkins do |jenkins|
    jenkins.vm.box = "centos/7"
    jenkins.vm.hostname = "jenkins"
    jenkins.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
    jenkins.vm.network "private_network", ip: "192.168.1.5"
    config.vm.provision 'shell', path: 'provision.sh'
    jenkins.vm.provider "libvirt" do |libvirt|
      libvirt.cpus = "2"
      libvirt.memory = "1024"
      libvirt.default_prefix = ""
    end
  end
end