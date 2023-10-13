# Package


## Executable JAR
JARs created by Maven : Packages the code

JARs created by Quarkus: Code + dependencies + runtime

Three types of Quarkus JAR :
- JAR a.k.a Fast-JAR : adds an index to speed up classpath scanning
- Legacy JAR a.k.a JAR (default) : packages the application code and the Quarkus runtime (without the index)
- Uber-JAR a.k.a Fat-JAR : contains all the classes of all dependencies

## Packaging and excecuting JARs
Fast-JAR
````
$ mvn package

equals as
$ mvn package -Dquarkus.package.type=jar
````

Legacy JAR
````
$ mvn package -Dquarkus.package.type=legacy-jar
````

Fat-JAR
````
$ mvn package -Dquarkus.package.type=uber-jar
````


## Executing JAR
Run %prod profile
````
$ java -jar target/quarkus-app/quarkus-run.jar
````

Run uber Jar
````
java -jar .\target\rest-demo-1.0.0-SNAPSHOT-runner.jar
````

Run with other profiles
````
$ java -Dquarkus.profile="staging" -jar target/quarkus-app/quarkus-run.jar

$ java -Dquarkus.profile=staging,dev -jar target/quarkus-app/quarkus-run.jar
````

## Building Native Executables

https://www.graalvm.org/reference-manual/native-image

Executable JARs contain byetcode : JARs need the JVM to run

Native images contain binary : The needed JVM is bundled inside this binary. This is very small executables, the compilation is resource intensive

## Building and executing a binary

````
$ mvn package -Dquarkus.package.type=native
$ mvn package -DskipTests -Dquarkus.package.type=native

or simple (-P for profile)
$ mvn package -Pnative
````

Executing
````
$ ./target/rest-demo-runner
$ target/rest-demo-1.0.0-SNAPSHOT-runner.exe -Dquarkus.banner.enabled=false
````

## Containerizing executable JARs

https://quarkus.io/guides/container-image

Jib or Docker extensions
Jib does not need Docker running

### Docker extension need docker

Both Jib and Docker extensions use generated Dockerfiles. They build an image. Configure the image with Quarkus properties


Dockerfile for JAR
src/main/docker/Dockerfile.jvm
````
FROM registry.access.redhat.com/ubi8/openjdk-17:1.16
````

## Build docker image
 
Add docker extension
````
$ mvn quarkus:add-etension -Dextensions="docker"
````

### Build docker image
Build docker image, by default this will run the Dockerfile.jvm
````
$ mvn package -Dquarkus.container-image.build=true

This equals to
$ mvn package -Dquarkus.container-image.build=true -Dquarkus.package.type=jar
````

If we want to use legacy-jar
````
$ mvn package -Dquarkus.container-image.build=true -Dquarkus.package.type=legacy-jar
````

To change the tag of image
````
$ mvn package -Dquarkus.container-image.build=true -Dquarkus.package.type=jar -Dquarkus.container-image.tag=jvm
````

Run docker images
````
$ docker run -i --rm -p 8701:8701 toan/rest-demo:1.0.0-SNAPSHOT
````


## Containerizing native linux executables

https://quarkus.io/guides/building-native-image

If you are in Linux
````
$ mvn package -Dquarkus.container-image.build=true -Dquarkus.package.type=native
````

If you are in Windows, this command will build a native linux in the docker
````
$ mvn package -Dquarkus.container-image.build=true -Dquarkus.package.type=native -Dquarkus.native.container-build=true
````

build and change docker tag
````
$ mvn package -Dquarkus.container-image.build=true -Dquarkus.package.type=native -Dquarkus.native.container-build=true -Dquarkus.container-image.tag=native
````

Build native 
``````
$ mvn package -Dquarkus.package.type=native -DskipTests=true -Dquarkus.native.container-build=true -Dquarkus.comtainer-image.build=true
``````


Verify and delete old docker image
````
$ docker image ls | grep rest
$ docker image rm 1364f571baa2
````

Run docker images
````
$ docker run -i --rm -p 8701:8701 toan/rest-demo:1.0.0-SNAPSHOT
````

