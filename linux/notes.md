# Linux

## Commands

### Search Port

Search process by port
````
$ sudo ss -lptn 'sport = :5432'
````

### Install java

````
$ sudo apt-get update
$ sudo apt-cache search java
$ sudo apt-get install openjdk-21-jdk openjdk-21-jre openjdk-21-source

$ sudo update-alternatives --config java
````
