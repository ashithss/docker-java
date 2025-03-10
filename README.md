# Java and Maven Version
```
java --version
openjdk 11.0.26 2025-01-21
OpenJDK Runtime Environment (build 11.0.26+4-post-Ubuntu-1ubuntu122.04)
OpenJDK 64-Bit Server VM (build 11.0.26+4-post-Ubuntu-1ubuntu122.04, mixed mode, sharing)

```

```
mvn --version
Apache Maven 3.6.3
Maven home: /usr/share/maven
Java version: 11.0.26, vendor: Ubuntu, runtime: /usr/lib/jvm/java-11-openjdk-amd64
Default locale: en_IN, platform encoding: UTF-8
OS name: "linux", version: "6.8.0-52-generic", arch: "amd64", family: "unix"
```

## Steps to run application
```
cd docker-java
mvn clean package
cd target
java -jar demo-java11-0.0.1-SNAPSHOT.jar

Your application will run in 8080 Port:- http://localhost:8080/
```

## Write an own Dockerfile and steps to run

```
docker build -t docker-demo-java .
docker run -d -p 8080:8080 --name=java-application docker-demo-java:latest
```


🎉