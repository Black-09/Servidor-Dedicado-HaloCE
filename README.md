![stability-wip](https://img.shields.io/badge/stability-unstable-lightgrey.svg)
<img src="https://i.imgur.com/zRXWDEK.png" width="190" height="164" align="right"/>

# Halo CE Servidor Dedicado en Docker

## Acerca de

Este es un archivo Docker para ejecutar el servidor dedicado de Halo CE en Linux. El contenedor utiliza Wine para ejecutar la aplicación de Windows y xvfb para crear un escritorio virtual.

El contenedor se ejecuta 100% - no se requiere una GUI para la instalación, ejecución o configuración.

***Esto es una version adaptada y mejorada de antimomentum*** https://github.com/antimomentum/haloce
##
# Programas necesarios
      FileZilla.
      Instalar la Districion 18.04 de linux.

##
## Alguien está DDOSing servidores de halo. 
ayuda relevante si tu servidor esta siendo atacado por DDoS

https://opencarnage.net/index.php?/topic/8149-halo-ce-servers-ddos/
##
# Pasos para crear tu Servidor Dedicado de Halo CE

 1. Renta un VPS de $5 dolares no esta mal para empezar y hacer pruebas.
 2. Actualizar los repositorios de Linux mediante / apt update   
 3. Instalar Docker en  el VPS / apt-get install docker.io      
 4. Clonar el este repositorio al VPS /  git clone https://github.com/Black-09/Servidor-Dedicado-HaloCE  
 5. Ingresar al directorio donde se aloja el repositorio / cd Servidor-Dedicado-HaloCE      
 6. construir el nuevo contenedor de Docker / docker build .     
 7. Ejecutar Nuestro servidor / docker run -it -p 2302:2302/udp [Codigo Generado cuando se construye el nuevo contenedor]
      

# Pasos para hacer cambios a tu Servidor Dedicado de Halo CE
##
 1. Reiniciar el VPS
 2. Abrir FileZilla y Conectarse al vps.
 3. Buscar la carpeta Servidor-Dedicado-HaloCE
 4. En la carpeta halopull se encuenta los archivos de ejecucion del servidor, en la carpeta de Halo CE estan los GameTypes y configuraciones secundarias del servidor SAPP.
 5. Despues de hacer los cambios... cerrar FileZilla.
 6. Es necesario volver a reconstruir elcontenedor de Docker, para eso debemos estar dentro del directorio [cd Servidor-Dedicado-HaloCE] y ejecutar el comando docker build .
 7. Ejecutar el servidor nuevamente con el comando / docker run -it -p 2302:2302/udp [Codigo Generado cuando se construye el nuevo contenedor]



     
    
     

    

