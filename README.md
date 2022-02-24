# Instalación de WordPress + Mysql + Nginx + SSL. Todo ello con docker-compose.
### Autor del docker compose
Link vídeo Youtube: 
https://youtu.be/6DqbEBda7Lc

URL autor: 
https://labarta.es/

URL del artículo:
https://labarta.es/instalar-wordpress-mysql-nginx-y-ssl-con-docker-compose/



**Nota: Para la instalación de Docker sigue los siguientes pasos:**

## Instalación de Docker

Eliminaremos alguna instalación previa de docker :

    sudo apt-get remove docker docker-engine docker.io containerd runc
    
Actualizacmos el repositorio

    sudo apt-get update

Instalamos lo certficados necesarios

    sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

Añadimos las llaves oficiales de docker
  
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

Utilice el siguiente comando para configurar el repositorio estable. Para agregar el repositorio nightly o test, agregue la palabra nightly o test (o ambas) después de la palabra estable en los comandos a continuación. Más información sobre los canales nocturnos y de prueba.

    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Actualizamos el registro de paquetes

    sudo apt-get update

Instalamos docker engine en su ultima versión disponible

    sudo apt-get install docker-ce docker-ce-cli containerd.io

Para comprobar la instalación podemos usar el siguiente comando: 

    sudo docker run hello-world

Usar docker sin sudo: 

    sudo usermod -aG docker $USER
    
***si realizas la instalación en alguna unidad cloud como Google Cloud, Azure o Digital Ocean es necesario que cierres la consola de comandos y vuelvas a iniciarlar, dado que no podras reiniciar la maquina como se hace normalmente en tu computador fisico***

## Instalar Docker Compose

Descargamos la versión estable de docker compose

    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Aplicamos los permisos al binario

    sudo chmod +x /usr/local/bin/docker-compose

Comprobamos que todo esta listo 
    
    docker-compose --version
    
***a la fecha de esta descripción el resultado del comando anterior es: ***
docker-compose version 1.29.2, build 5becea4c


