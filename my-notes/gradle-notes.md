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

#### Gradle wrapper 

There are two different Gradle applications in your system.

* The system-wide Gradle : This application is invoked by gradle (arguments).
```
gradle
```

* The gradle-wrapper:  The gradle-wrapper is specific to every project and can only be invoked inside the project's directory, using the command. It uses all information in the gradle/wrapper directoty to pull an specific version of gradle and its local settings in the **gradle-wrapper**.properties 
for instance: distributionUrl=https\://services.gradle.org/distributions/gradle-7.2-bin.zip


```
./gradlew (arguments).

```

Generate specific gradle wrapper version, for instance 5.1.1

for instance 5.1.1
```
gradle --version
gradle wrapper --gradle-version=5.1.1  

```

* Common error 
```
Deprecated Gradle features were used in this build, making it incompatible with Gradle 7.0.
```
It means that your wrapper is a diferent version of the current gradle or vice versa and there are some deprecated features. 
Compare your local gradel with the gradle wrapper. 

```
 gradle --version 
 ./gradlew wrapper --version;
```
#### Change gradle version manually 

Go to  ccpay-payment-app/gradle/wrapper/gradle-wrapper.properties file .

there is distributionUrl=https\://services.gradle.org/distributions/gradle-5.6-all.zip  there you can change your gradle file to use a particular version.

```
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-5.6-all.zip
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists

```

