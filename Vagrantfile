# Configuración de Vagrantfile para crear una VM con Apache
Vagrant.configure("2") do |config|
  # Usar una imagen base de Ubuntu
  config.vm.box = "ubuntu/bionic64"

  # Configuración de la red y recursos
  config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"       # Asignar 512MB de RAM
    vb.cpus = 1             # Asignar 1 CPU
  end

  # Instalación y configuración de Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    echo "<h1>Hola Mundo</h1>" | sudo tee /var/www/html/index.html
  SHELL

  # Configuración para compartir la carpeta local con el directorio de Apache
  config.vm.synced_folder ".", "/var/www/html", type: "virtualbox"
end
