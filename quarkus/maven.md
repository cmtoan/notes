## Run

Run with profile "demo"

```
$ mvn -Dquarkus.profile=demo quarkus:dev
```

## Build native

```
$ mvn package -Pnative

$ mvn package -Pnative -DskipTests=true -Dquarkus.native.additional-build-args="--initialize-at-run-time=org.apache.http.impl.auth.NTLMEngineImpl"
```
