# PiAlert | Detección "intrusos" en red WiFi y LAN
docker-compose de PiAlert | Detección "intrusos" en red WiFi y LAN
## Pasos a seguir
#PiAlert | Genbyte | https://www.youtube.com/@genbyte

mkdir ~/docker/pialert -p

sudo chown "$USER":"$USER" ~/docker -R #Permisos al usuario en la carpeta Docker

docker run -d --name=pialert --net=host -e TZ=Europe/Madrid jokobsk/pi.alert:23

docker cp pialert:/home/pi/pialert/config ~/docker/pialert/

docker cp pialert:/home/pi/pialert/db ~/docker/pialert/

docker rm pialert --force

#Desplegar contenedor con "run" o bien con docker-compose <p>
docker run -d --name=pialert --net=host -e TZ=Europe/Madrid -v ~/docker/pialert/db:/home/pi/pialert/db -v ~/docker/pialert/config/:/home/pi/pialert/config/ --restart=unless-stopped jokobsk/pi.alert

<br>
## Acceso vía web

http://localhost:20211

