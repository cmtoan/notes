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
          --initialize-at-run-time=org.apache.http.impl.auth.NTLMEngineImpl\,com.amazonaws.retry.PredefinedBackoffStrategies$FullJitterBackoffStrategy\,com.amazonaws.auth.BaseCredentialsFetcher\,com.amazonaws.retry.PredefinedBackoffStrategies$EqualJitterBackoffStrategy\,java.util.concurrent.Executors$AutoShutdownDelegatedExecutorService\,com.amazonaws.event.SDKProgressPublisher$LazyHolder\,com.amazonaws.retry.PredefinedBackoffStrategies\,com.amazonaws.retry.PredefinedBackoffStrategies$SDKDefaultBackoffStrategy\,com.amazonaws.retry.PredefinedRetryPolicies\,com.amazonaws.retry.RetryPolicy\,com.amazonaws.ClientConfiguration\,com.amazonaws.auth.InstanceProfileCredentialsProvider\,com.amazonaws.auth.EC2ContainerCredentialsProviderWrapper\,com.amazonaws.auth.AWSCredentialsProviderChain
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
      <groupId>software.amazon.msk</groupId>
      <artifactId>aws-msk-iam-auth</artifactId>
      <version>2.0.2</version>
      <exclusions>
        <exclusion>
          <groupId>commons-logging</groupId>
          <artifactId>commons-logging</artifactId>
        </exclusion>
      </exclusions>
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

### register for reflection
``` java
@RegisterForReflection(
  targets = {
    IAMLoginModule.class,
    IAMClientCallbackHandler.class,
    IAMSaslClient.ClassLoaderAwareIAMSaslClientFactory.class,
    IAMSaslClient.IAMSaslClientFactory.class,
    AuthenticationResponse.class,
  }
)
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

### reference

https://quarkus.io/guides/building-native-image [https://quarkus.io/guides/building-native-image]

https://quarkus.io/guides/writing-native-applications-tips [https://quarkus.io/guides/writing-native-applications-tips]

https://stackoverflow.com/questions/63328298/how-do-you-debug-a-no-instances-of-are-allowed-in-the-image-heap-when-buil [https://stackoverflow.com/questions/63328298/how-do-you-debug-a-no-instances-of-are-allowed-in-the-image-heap-when-buil]

