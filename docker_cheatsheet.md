Resumen de Comandos en Docker
========================

###DOCKER ENGINE
- **docker images** &rarr; lista las imágenes instaladas localmente
- **docker images --digests** &rarr; listar imágenes con su digest (para versiones con formato V2 y posterior)
- **docker run -t -i ubuntu:14.04 /bin/bash** &rarr; ejecutar un contenedor (ejemplo de ubuntu 14.04, por defecto siempre será latest)
- **docker run -t -i ubuntu:12.04 /bin/bash** &rarr; ejecutar un contenedor (ejemplo de ubuntu 12.04, por defecto siempre será latest)
- **docker run -t -i &lt;repository&gt;:&lt;tag&gt; /bin/bash** &rarr; 
- **docker run -itd --name=container1 busybox** &rarr; ejecutar un contenedor, asignandole un nombre  con las opciones (t:allocate a psedo tty, d: detached, i: keep STDIN open even if not attached)
- **docker pull &lt;image&gt;** &rarr; pre-load una imagen sin ejecutarla
- **docker pull &lt;image&gt;@digest** &rarr; pull con digest (p.e. docker pull ouruser/sinatra@sha256:cbbf2f9a99b47fc460d422812b6a5adff7dfee951d8fa2e4a98caa0382cfbdbf) e
- **docker search** &rarr; buscar una imagen en el docker hub (ej. docker search sinatra)
- **docker commit -m "texto" -a "autor" &lt;ID&#95;of&#95;image&gt; &lt;target&#95;for&#95;image&gt;** &rarr; Actualizar una imagen con los cambios aplicados dentro del container (p.e. docker commit -m "Added json gem" -a "Kate Smith" \ 0b2616b0e5a8 ouruser/sinatra:v2 )
- **docker build -t &lt;user&gt;/&lt;target&#95;for&#95;image&gt; .** &rarr; (ejecutar en el directorio donde esté el dockerfile) (p.e. docker build -t ouruser/sinatra:v2 .)
- **docker tag &lt;id&gt; &lt;user&#95;name&gt;/&lt;target&#95;for&#95;image&gt;** &rarr; hacer un tag a un estado de la imagen (p.e. docker tag 5db5f8471261 ouruser/sinatra:devel)
- **docker push &lt;imagen&gt;** &rarr; subir la imagen a Docker hub o un repositorio privado (p.e. docker push ouruser/sinatra)
- **docker rmi &lt;target&#95;for&#95;imagen&gt;** &rarr; borrar una imagen de tu host local (p.e. docker rmi training/sinatra)
- **docker rm &lt;container&gt;** &rarr; borrar un contenedor

- **docker rm `docker ps -aq -f status=exited`** &rarr; ﻿Borrar todos los contenedores que no están en ejecución

- **docker stop &lt;container&gt;** &rarr; detener un container
- **docker start &lt;container&gt;** &rarr; iniciar un container
- **docker restart &lt;container&gt;** &rarr; reiniciar un container
- **docker ps** &rarr; lista los contenedores
- **docker ps -l** &rarr; listar los containers en ejecución
- **docker ps -a** &rarr; listar todos los containers del sistema
- **docker ps -a -f status=running** &rarr; listar los contenedores en estado running mediante un filtro
- **docker logs** &rarr; muestra la salida estandar de un contenedor
- **docker version** &rarr; lista la versión actual instalada
- **docker --help** &rarr; lista la ayuda con los posibles comandos
- **docker &lt;comando&gt; --help ** &rarr; ayuda para un comando específico
- **docker run -d -P training/webapp python app.py** &rarr; ejecutar una webapp (-d ejecutar en background, -P mapear cualquier puerto necesario dentro de nuestro container a nuestro host)
- **docker run -d -p 80:5000 training/webapp python app.py** &rarr; ejecutar una webapp especificando el puerto
- **docker-machine ip your&#95;vm&#95;name** &rarr; obtener la ip de tu virtual machine
- **docker port &lt;Id&gt; &lt;puerto&gt;** &rarr; devuelve el mapeo de puerto para un container y un puerto específico (p.e. docker port nostalgic&#95;morse 5000 =&gt; 0.0.0.0:49155)
- **docker logs -f nostalgic&#95;morse** &rarr; ver los logs de la webapp del container
- **docker top nostalgic&#95;morse** &rarr; ver los procesos ejecutándose en nuestro container
- **docker inspect &lt;container&gt;** &rarr; devuelve información importante sobre el container
- **docker attach &lt;id&gt;/&lt;name&gt;** &rarr; hacer ssh (entrar en el shell) del container ejecutandose en segundo plano.
- **ctrl-p + ctrl-q** &rarr; Salir de un attach y dejarlo ejecutándose
- **docker exec -i -t &lt;id&gt;/&lt;name&gt; /bin/bash** &rarr; entrar en el shell de un container (permite más de un shell)
- **docker cp foo.txt mycontainer:/foo.txt** &rarr; copiar un archivo del host al container
- **docker cp mycontainer:/foo.txt foo.txt** &rarr; copiar un archivo del container al host
- **docker rm `docker ps -qa`** &rarr; borrar todos los containers
- **export TERM=xterm** &rarr; Ejecutar esto en un container para poder ejecutar nano
- **docker exec -it [CONTAINER&#95;ID] /bin/bash -c "export TERM=xterm; exec bash"** &rarr; lo mismo que el comando anterior desde fuera
- **/sbin/ip route|awk '/default/ { print $3 }'** &rarr; ver dirección ip del host desde el container
- **docker network ls** &rarr; Listar las redes creadas por docker por defecto
- **docker network inspect bridge** &rarr; Inspeccionar la red "bridge" creada por defecto por docker en los host de docker





### DOCKER-COMPOSE

- **docker-compose stop** &rarr; parar los containers del archivo docker-compose.yml
- **docker-compose build** &rarr; vuelve a construir la imagen si existe algún comando build dentro del docker-compose.yml
- **docker-compose up -d** &rarr; levanta los containers del docker-compose.yml en estado detached, para que no se paren al salir.
- **docker-compose build && docker-compose up -d** &rarr; concatenar los dos comandos anteriores



### DOCKER SWARM

- **docker service create --replicas 2 --network my-multi-host-network --name my-web nginx** &rarr; Crear un servicio nginx extendiendo la red "my-multi-host-network" a los nodos donde los servicios o tareas de los servicios se ejecutan
- **docker network create --driver overlay my-multi-host-network** &rarr; Crear una red de tipo "overlay" en una de las máquinas de swarm
- **docer run -itd --network=mymulti-host-network busybox** &rarr; Lanzar un contenedor en un host de swarm especificando la red overlay

### DOCKER SWAP MEMORY PROBLEM

- **Make swap memory on host machine using a swap file.**&rarr; https://getcomposer.org/doc/articles/troubleshooting.md#proc-open-fork-failed-errors