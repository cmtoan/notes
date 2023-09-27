# Images docker

## Create an docker image

Create an image Docker from a Dockerfile
````
$ docker image build [OPTIONS] PATH | URL | -
````

(before, the command is : docker build)

Common options

-f : specify a file to use to build (by default Dockerfile)

--tag / -t : specify image name ([registry/]user/repository:tag)
--label : add meta data to image

ex:
````
$ docker image build -t app:1.0
````

Exemple : application Java

````java
public class Main
{
    public static void main(String[] args) {
        System.out.println("Hello, World");
    }
}
````

Dockerfile
````
FROM openjdk:10

COPY . /usr/src/myapp

WORKDIR /usr/src/myapp

RUN javac Main.java

CMD ["java", "Main"]
````

Build then run image
````
$ docker image build -t hellojava:v1.0 .
$ docker container run hellojava:v1.0
````

## Common commands

````
$ docker image --help
````

Download an image
````
$ docker image pull alpine
````
format of image name : USER/IMAGE:VERSION


View detail of image

````
$ docker image inspect alpine

$ docker image inspect -f '{{ .Architecture }} alpine

$ docker inspect --format '{{ .ContainerConfig.Cmd }}' mongo:3.2
````

History of image
````
$ docker history alpine
````

List present image in local (created or downloaded)
````
$ docker image ls
$ docker images
````

List also created images when building
````
$ docker image ls -a
````

filter images by name
````
$ docker image ls node
````

List id of rested images
````
$ docker image ls -q
````

List all images in dangling state (images "dangling" are not referenced)
````
$ docker image ls --filter dangling=true
````

Theses images can be deleted by command prune (delete images "dangling")
````
$ docker image prune
````

export an image in a file tar
````
$ docker save -o alpine.tar alpine
````

Delete image alpine in local
````
$ docker image rm alpine
````

Delete many images at the same time
````
$ docker image rm $(docker image ls -q)
````

Create an image from a tar file (must in a format attended by docker deamon)
````
$ docker load < alpine.tar
````

## Registry image docker

Docker Hub

Docker Registry

Docker Trusted Registry
````
$ docker image push IMAGE
$ docker image pull IMAGE
````

Run a registry in a container
````
$ docker container run -d -p 5000:5000 registry:2.6.2
````

List present images in the registry
````
$ curl localhost:5000/v2/_catalog
````


Tag nginx image with format URL:PORT/NAME:VERSION
````
$ docker image tag nginx:1.14 localhost:5000/nginx:1.14
````

upload image into registry
````
$ docker image push localhost:5000/nginx:1.14
````

## Configure registry in local

Example
````
$ vim /lib/systemd/system/docker.service

ExecStart=/usr/bin/dockerd -H fd:// --insecure-registry 192.168.33.11:5000
````

Restart daemon docker
````
$ systemctl daemon-reload
$ systemctl restart docker
````

Then push image
````
$ docker image push 192.168.33.11:5000/nginx:1.14
````

Another way to do
````
$ vim /etc/docker/daemon.json
{
	"insecure-registries": ["192.168.33.11:5000"]
}
````

Then restart docker and push image
````
$ systemctl restart docker
$ docker image push 192.168.33.11:5000/nginx:1.14
````

