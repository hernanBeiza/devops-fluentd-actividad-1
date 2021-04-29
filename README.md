# devops-fluentd-actividad-1
 Actividad 1 de Fluentd en Diplomado DevOps Usach.


## Requerimientos

- docker

## Ejecutar

- Bajar imagen

````
docker pull fluentd
````

- Crear volumen docker

```
docker volume create fluentd-vol 
```

- Correr docker con configuración

````
docker run --name fluentd -d -p 24224:24224 -p 24224:24224/udp -u fluent -v fluentd-vol:/Volumes/fluentd/log -v <ruta completa>/archivo.conf:/fluentd/etc/fluent.conf fluentd 
````

## Iniciar sesión SSH

- Obtener id contenedor

```
docker ps
```

- Iniciar sesión ssh en el contenedor

````
docker exec -it <id contenedor> /bin/sh
````

- Iniciar sesión ssh en el contenedor como root

```
docker exec -it -u root <id contenedor> /bin/sh
```

## Probar

````
curl -X POST -d 'json={"foo":"bar"}' http://localhost:24224/app.log
````

## Revisar log

```
docker ps
```

````
docker exec -it <id contenedor> /bin/sh
````

- En el contenedor

```
cd /Volumes/fluentd/log
```

