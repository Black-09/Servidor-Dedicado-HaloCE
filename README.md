![stability-wip](https://img.shields.io/badge/stability-unstable-lightgrey.svg)
<img src="https://i.imgur.com/zRXWDEK.png" width="190" height="164" align="right"/>

# Halo CE Servidor Dedicado en Docker

## Acerca de

Este es un archivo Docker para ejecutar el servidor dedicado de Halo CE en Linux. El contenedor utiliza Wine para ejecutar la aplicación de Windows y xvfb para crear un escritorio virtual.

El contenedor se ejecuta 100% - no se requiere una GUI para la instalación, ejecución o configuración.

## Alguien está DDOSing servidores de halo. 
ayuda relevante si tu servidor esta siendo atacado por DDoS

https://opencarnage.net/index.php?/topic/8149-halo-ce-servers-ddos/

## Pasos para crear tu Servidor Dedicado de Halo CE


## 1. Renta un VPS de $5 dolares no esta mal para empezar y hacer pruebas.

## 2. Actualizar los repositorios de Linux mediante.
      apt update
      
## 3. Instalar Docker en  el VPS.
      apt-get install docker.io
      
## 4. Clonar el este repositorio al VPS.
      git clone https://github.com/Black-09/Servidor-Dedicado-HaloCE
      
## 5. Ingresar al directorio donde se aloja el repositorio.
      cd Servidor-Dedicado-HaloCE
      
## 6. construir el nuevo contenedor de Docker.
      docker build .

## 7. Ejecutar Nuestro servidor.
      docker run -it -p 2302:2302/udp [Codigo Generado cuando se construye el nuevo contenedor]


Now copy in the haloceded.exe, Strings.dll, sapp.dll (basically whatever is from you Program Files\Micorosft Games\Halo Custom Edition folder) in the halopull folder.
For sapp, also copy your My Documents\My Games\Halo CE stuff in the 'Halo CE' folder.


Then do:

docker build . 

You should see something like: "Successfully built f01ecb978acc" <---- the f01ecb is the docker image you need to start the container. So do:

docker run -it -p 2302:2302/udp f01ecb978acc 

with the f01ecb replaced with whatever ID you got from the docker build :) 

##  Push your halo server images to docker!

docker build -t YourDockerUsername/MadeUpImageName . 

apt-get install gnupg

docker login

docker push YourDockerUsername/MadeUpImageName

## What's that? Copy files to a linux server?


If you're not familiar with command line linux and aren't sure how to get your custom files
to your server, Filezilla makes this pretty easy. Most cloud providers like Linode and DigitalOcean provide ssh access
and port access by default. 
So in Filezilla on your Windows PC enter do this:
For host enter the IP address of your server
Username: root
password is whatever root password you made on your cloud provider dashboard
port is 22
The haloce folder is probably under /root/haloce


## Step by step example 


At cloud.linode.com/linodes click Add a Linode

Under Choose a Distribution pick Ubuntu 18 LTS

For Linode plan pick Nanode 1GB

Type in a Root Password and then click create

After it provisions and boots up click on it. You should see "Launch Console" to the right of the page. Click that

Login as: root

with the password you typed in

Then issue:

apt update

apt upgrade

apt-get install docker.io

docker run -it -p 2302:2302/udp antimomentum/haloce

Wait for it to build and boot

sv_name "Test Container"

You can now find it in the game server list from the game client :)  Make sure your halo server list isn't filtering empty servers!

Here are some sapp commands:

pl

map


## But wait! There's more! Automated Installs of YOUR server files!

So if you sucessfully built and ran a container with your own custom server files you might be wondering: "Well, if I buillt my own container what do I need the antimomentum/haloce container for?"

The answer is you don't!

To push your own container image to Docker make a docker account on the docker website. A free account is fine and is what I'm using.


Make sure your container halo server isn't currently running. docker ps will show running containers. docker stop containerid will close the container.


Now tag your image. 

docker build -t dockerusername/imagename .


Don't forget the . there! Also, the imagename can be whatever you make up for it.


next install this:


apt-get install gnupg


Then login to docker:


docker login


then push your custom server image to docker!


docker push dockerusername/imagename


To download your image to a new server:


apt update


apt-get install docker.io


docker run -it -p 2302:2302/udp dockerusname/imagename


Done :)


Want to run multiple servers?


apt-get install -y screen


screen -S halo1 docker run -it -p 2304:2304 dockerusername/imagename wineconsole haloceded.exe -port 2304

You'll notice all the ports match each other. (In order it's: hostport:dockerport and at the end of the command is wineconsole telling halo which port it needs). For the next server make sure it has its own port that matches too, and just repeat


screen -S halo2 docker run -it -p 2308:2308 dockerusername/imagename2 wineconsole haloceded.exe -port 2308


In other words all you have to do is make an image for EACH halo server once. After that you can run them simply by specifying the image name and port like we just did here!


Side Note: Some cloud providers already use Screen for the web interface. IF screen is already installed and you're using Windows, download Putty and try apt-get install screen
You'll notice screen actually installed itself this time, and that will allow you to use the screen keyboard shortcuts! :)


## Some basic cloud services info
## This section is about to get a major change

Cloud services such as AWS, Google CLoud, and Azure have security rules outside the host operating system you need to configure to allow your server to communicate with the internet. You need to allow ports: 22 and 2302.
(Note: My firewall blocks tcp, you will need to alter it to accept your IP above the PREROUTING rules for ssh to work for you)


service ssh stop


Note: disabling ssh may disable access to your server on AWS, Gcloud, Azure. On linode/DO the Launch Console still gives access to your server. 


On your actual cloud service account, enable 2 factor authentication and set a complex password.

## Thanks and Resources ##

Special thanks to:

AugusDogus

Chalwk77 https://github.com/Chalwk77/HALO-SCRIPT-PROJECTS

Devieth
http://halopc.com/sv_extensions/

.þsϵυdø.þrø×϶n

Crash
https://theashclan.org/

Chimera http://vaporeon.io/hosted/halo/chimera/ 

Everyone else involved in helping make Halo more awesome
