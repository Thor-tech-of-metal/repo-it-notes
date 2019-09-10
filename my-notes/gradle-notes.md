#### print gradle version

```
gradle build -version
```
#### Building locally
```
gradle clean build  --info
```

#### Build and skip test
```
./gradlew clean build -x test --info
```

#### Build and force to build all files
```
./gradlew clean build --info --rerun-tasks
```

#### Publish locally
```
./gradlew clean build install --info
```

#### Publish nexus
```
./gradlew upload --info
```

#### When gradle get locks
```
1) gradle --status
2) gradle --stop
```

#### modules
```
gradle clean  module:taskName --info

gradle clean  api:clean build --info
```


#### Print dependencies tree compile

```
./gradlew  dependencies --configuration compile
```

#### Print dependencies
```
./gradlew  dependencies --configuration compile
```

#### Make gradle use one particular VM

Change gradle.properties in stub project add

org.gradle.java.home=/Library/Java/JavaVirtualMachines/jdk1.8.0_162.jdk/Contents/Home


#### Start spring servers
```
gradle bootRun
```

#### check dependency security

```
/gradlew clean  -DdependencyCheck.failBuild=true  -Dcve.check.validforhours=24 -Danalyzer.retirejs.enabled=false dependencyCheckAnalyze --info
````

#### Building locally your docker image.


./gradlew clean build buildDocker --stacktrace --info

