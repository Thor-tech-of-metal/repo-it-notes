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

#### Build and  execute one particular test
```
./gradlew test --tests uk.gov.hmcts.ccd.domain.service.callbacks.CallbackServiceWireMockTest
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

#### Gradle properties

This is located in $HOME/.gradle/gradle.properties

#### Make gradle use one particular VM

Change gradle.properties in stub project add

org.gradle.java.home=/Library/Java/JavaVirtualMachines/jdk1.8.0_162.jdk/Contents/Home

#### Add more memory to gradle global 

Change in $HOME/.gradle/gradle.properties

org.gradle.jvmargs=-XX:MaxHeapSize=256m -Xmx256m

#### Make gradle not use deamon thread  and resolve posible memory issues in old VM
```
./gradlew clean --no-daemon build 
```

#### Start spring servers
```
gradle bootRun
```

#### check dependency security

```
./gradlew clean  -DdependencyCheck.failBuild=true  -Dcve.check.validforhours=24 -Danalyzer.retirejs.enabled=false dependencyCheckAnalyze --info
````

#### Building locally your docker image.

```
./gradlew clean build buildDocker --stacktrace --info
```



#### Add module compile dependecies 

```
dependencies {
    compile project(':app-insights')
    compile project(':rest-api')
    compile project(':excel-importer')
    
    testCompile project(":app-insights").sourceSets.main.output
} 
```
