Vagrant.configure("2") do |config|
  # Usar una caja de Ubuntu
  config.vm.box = "ubuntu/bionic64"

  # Mapea el puerto 80 del servidor Apache en la VM al puerto 8080 en el host
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Asignar recursos de la máquina virtual
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"  # 512 MB de RAM
    vb.cpus = 1        # 1 CPU
  end

  # Configuración de la carpeta compartida
  config.vm.synced_folder "./apache-web", "/var/www/html"

  # Provisionar Apache dentro de la máquina virtual
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    echo '<h1>Hola, Mundo!</h1>' | sudo tee /var/www/html/index.html
    sudo systemctl enable apache2
    sudo systemctl start apache2
  SHELL
end

