Vagrant.configure("2") do |config|
  config.vm.network "private_network", type: "dhcp"  # Opción alternativa de red
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end
end
  # Configuración del servidor Apache
  config.vm.provision "shell", inline: <<-SHELL
    # Actualizamos el sistema
    sudo apt-get update -y
    sudo apt-get upgrade -y

    # Instalamos Apache
    sudo apt-get install apache2 -y

    # Creamos una página de prueba en el directorio por defecto de Apache
    echo '<html><body><h1>Hola Mundo desde Apache!</h1></body></html>' | sudo tee /var/www/html/index.html
  SHELL

  # Compartir la carpeta local con el directorio del servidor Apache
  config.vm.synced_folder "./pagina_web", "/var/www/html"
end

