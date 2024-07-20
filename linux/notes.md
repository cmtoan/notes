# Linux

## Commands

### Search Port

Search process by port
````
$ sudo ss -lptn 'sport = :5432'
````

### Lệnh which

Lệnh which sẽ hiển thị đường dẫn đến các tập tin chương trình (executable file).
Nó tìm trong các tập tin được liệt kê trong biến môi trường PATH.

````
$ which vim
$ ls -la $(which git)
````

### Install java

````
$ sudo apt-get update
$ sudo apt-cache search java
$ sudo apt-get install openjdk-21-jdk openjdk-21-jre openjdk-21-source

$ sudo update-alternatives --config java
````
