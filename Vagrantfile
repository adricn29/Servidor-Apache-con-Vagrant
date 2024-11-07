Vagrant.configure("2") do |config|
    # Especificar la box base
    config.vm.box = "ubuntu/focal64"
  
    # Configurar la cantidad de RAM y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
  
    # Configurar el aprovisionamiento para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
    SHELL
  
    # Compartir la carpeta del servidor web de Apache
    config.vm.synced_folder "./src", "/var/www/html"
  
    # Hacer que la VM exponga el puerto 80 al puerto 8080 del host
    config.vm.network "forwarded_port", guest: 80, host: 8080
  end
