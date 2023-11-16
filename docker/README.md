# Docker

## Commands

````
$ sudo systemctl start docker
$ docker info
````

Run container

````
$ docker container run hello-world
````

Run in mode interactive

````
$ docker container run -t -i ubuntu bash
````
-t : allocate a pseudo TTY

-i : keep STDIN open



````
$ docker container run -d -p 8080:80 nginx:1.14-alpine
````

-d : run docker in background (by default the container runs in foreground)

-p HOST_PORT:CONTAINER_PORT : to access to docker from outside or the option -P (allocate dynamically all the ports)



````
$ docker container run -v HOST_PATH:CONTAINER_PATH
$ docker container run --mount type=bind, src=HOST_PATH, dst=CONTAINER_PATH

````

 -v or --mount : to mount the file system of container to a file or a folder in host machine


## Docker container


List active containers

````
$ docker container ls
````

List active and stopped containers

````
$ docker container ls -a
````

List active and stopped containers' identities

````
$ docker container ls -a -q
````

View detail of docker (available for primitive dockers like container, image, volume, network ...)
````
$ docker container inspect 6df4
````


Use Go template
https://docs.docker.com/engine/reference/commandline/inspect/
````
$ docker container inspect --format '{{ .NetworkSettings.IPAddress }}' 6df4

$ docker container inspect --format '{{ json .State }}' 6df4 | jq
````

Stop a container

````
$ docker container stop ID
$ docker container stop NAME
$ docker container stop $(docker container ls -q)
````


Delete one or many containers (already stopped)

````
$ docker container rm ID
$ docker container rm NAME
$ docker container rm $(docker container ls -aq)
````


option -f (to force container to stop)
````
$ docker container rm -f 6df4
$ docker container rm -f $(docker container ls -aq)
````

To go into a docker
````
$ docker container ls

$ docker exec -i -t docker-kafka-1 bash
````

### Command for the life cycle of a container

- run : create a container
- ls : list the containers
- inspect : see details of a container
- logs : visualisation of logs
- exec : launch a process in a existing container
- stop : stop a container
- rm : suppression of container