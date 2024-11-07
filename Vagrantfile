# Vagrantfile
Vagrant.configure("2") do |config|

    # Configurar la caja de Ubuntu 22.04 
    config.vm.box = "ubuntu/jammy64"

    # Asignar un nombre a la mÃ¡quina virtual
    config.vm.hostname = "UnServer"

    # Configurar la red para poder acceder al servidor web 
    config.vm.network "private_network", ip: "192.168.56.25"

    # Asignar recursos a la VM
    config.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
        vb.cpus = 1
    end

    # Instalar Apache al iniciar la VM 
    config.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl enable apache2
    SHELL

    # Compartir la carpeta local con la carpeta de Apache 
    config.vm.synced_folder "src", "/var/www/html", owner: "www-data", group: "www-data"
    end
