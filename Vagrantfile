Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"  # Utiliza una box de Ubuntu
    config.vm.network "forwarded_port", guest: 80, host: 8080  # Mapea el puerto 80 del VM al 8080 del host
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"  # Asigna 512 MB de RAM
      vb.cpus = 1        # Asigna 1 CPU
    end
    
    # Configura la carpeta compartida
    config.vm.synced_folder "./paginas_web", "/var/www/html"  # Cambia este directorio si es necesario
    
    # Provisiona la máquina para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install -y apache2
      echo '<h1>Hola, Mundo!</h1>' | sudo tee /var/www/html/index.html
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
