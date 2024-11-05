Vagrant.configure("2") do |config|
    # Usar una imagen base de Ubuntu
    config.vm.box = "ubuntu/jammy64"
  
    # Configurar la cantidad de RAM y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
    end
  
    # Configurar el nombre de la máquina (opcional)
    config.vm.hostname = "apache-server"
  
    # Configurar la red
    config.vm.network "private_network", type: "dhcp"
  
    # Instalar Apache en la máquina virtual
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
    SHELL
  
    # Compartir la carpeta de Apache con el directorio local
    config.vm.synced_folder "./src", "/var/www/html", owner: "www-data", group: "www-data"
  
    # Hacer que la VM exponga el puerto 80 (de Apache) al puerto 8080 del host
    config.vm.network "forwarded_port", guest: 80, host: 8080
  end
  