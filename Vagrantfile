## 1. Definindo as características das máquinas virtuais 
jenkins = {
  'jenkins' => {'memory' => '1024', 'cpus' => 1, 'ip' => '50', 'box' => 'centos/7'},
}
## 1. Aplicando as configurações no virtualizador
Vagrant.configure('2') do |config|
  config.vm.box_check_update = false                                    ## opcional: adiar a checagem de updates
  config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
  jenkins.each do |name, conf|
    config.vm.define "#{name}" do |my|
      my.vm.provision 'shell', path: 'provision.sh'
      my.vm.box = conf['box']                                           ## seleciona a box com a distribuição linux a ser utilizada
      my.vm.hostname = "#{name}.example.com"                            ## define o hostname da máquina
      my.vm.network 'private_network', ip: "192.168.56.#{conf['ip']}"   ## define o ip de cada máquina de acordo com o range do Virtualbox
      my.vm.provider 'libvirt' do |vb|
        vb.memory = conf['memory']                                      ## define quantidade de recurso de memória
        vb.cpus = conf['cpus']                                          ## define quantidade de vCPUs
      end
    end
  end
end
