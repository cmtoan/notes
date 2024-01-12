
### skip jacoco

```
$ mvn clean install -Djacoco.skip=true
```

### quarkus

run with profile "demo"

```
$ mvn -Dquarkus.profile=demo quarkus:dev
```

build native

```
$ mvn package -Pnative -DskipTests=true 

$ mvn package -Pnative -DskipTests=true -Dquarkus.native.additional-build-args="--initialize-at-run-time=org.apache.http.impl.auth.NTLMEngineImpl"
```
