### Profiles

```
  <profiles>
    <profile>
      <id>native</id>
      <activation>
        <property>
          <name>native</name>
        </property>
      </activation>
      <properties>
        <skipITs>false</skipITs>
        <quarkus.package.type>native</quarkus.package.type>
        <quarkus.native.additional-build-args>
          --initialize-at-run-time=org.apache.http.impl.auth.NTLMEngineImpl
        </quarkus.native.additional-build-args>
      </properties>
    </profile>
  </profiles>
```

### Resolve dependencies

```
    <dependency>
      <groupId>org.jboss.logmanager</groupId>
      <artifactId>log4j-jboss-logmanager</artifactId>
    </dependency>
    <dependency>
      <groupId>org.jboss.logmanager</groupId>
      <artifactId>log4j2-jboss-logmanager</artifactId>
    </dependency>
    <dependency>
      <groupId>org.jboss.logging</groupId>
      <artifactId>commons-logging-jboss-logging</artifactId>
    </dependency>
    <dependency>
      <groupId>org.jboss.slf4j</groupId>
      <artifactId>slf4j-jboss-logmanager</artifactId>
    </dependency>
    <dependency>
      <groupId>io.quarkiverse.amazonservices</groupId>
      <artifactId>quarkus-amazon-common</artifactId>
      <version>2.9.0</version>
    </dependency>
    <dependency>
      <groupId>io.quarkiverse.amazonservices</groupId>
      <artifactId>quarkus-amazon-sts</artifactId>
      <version>2.9.0</version>
    </dependency>
    <dependency>
      <groupId>joda-time</groupId>
      <artifactId>joda-time</artifactId>
      <version>2.12.6</version>
    </dependency>
    <dependency>
      <groupId>com.opencsv</groupId>
      <artifactId>opencsv</artifactId>
      <version>5.8</version>
      <exclusions>
        <exclusion>
          <groupId>commons-logging</groupId>
          <artifactId>commons-logging</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
```

### config quarkus

disable local stack

```
quarkus.sts.devservices.enabled=false
```

### command

```
$ mvn package -Pnative -DskipTests=true 

$ mvn package -Pnative -DskipTests=true -Dquarkus.native.additional-build-args="--initialize-at-run-time=org.apache.http.impl.auth.NTLMEngineImpl"
```
