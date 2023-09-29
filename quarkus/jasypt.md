# Smallrye Jasypt

pom.xml
````
    <dependency>
      <groupId>io.smallrye.config</groupId>
      <artifactId>smallrye-config-jasypt</artifactId>
      <version>3.4.0</version>
    </dependency>

````

````
$ java -classpath ~/.m2/repository/org/jasypt/jasypt/1.9.3/jasypt-1.9.3.jar org.jasypt.intf.cli.JasyptPBEStringEncryptionCLI input="toto" password=jasypt algorithm=PBEWithHMACSHA512AndAES_256 ivGeneratorClassName=org.jasypt.iv.RandomIvGenerator
````

application.properties
````
smallrye.config.secret-handler.jasypt.password=jasypt
smallrye.config.secret-handler.jasypt.algorithm=PBEWithHMACSHA512AndAES_256

my.secret=${jasypt::ENC(bnZKlyfTdcGBMktYa0HfJS8JsGCVwW/WT2ombS/EGXQP6LnHi1gM0Pk4qSrzAp3y)}
````


https://smallrye.io/smallrye-config/Main/config/secret-keys/#crypto

