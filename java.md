###### convert .class to .java

```shell
$ cd ../WEB-INF/classes/com/sample/service/impl
$ javap -c MyServiceImpl
```

###### mvn generate

```shell
$ mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.sample -DartifactId=sample-common -Dversion=1.0-SNAPSHOT -Dpackage=com.sample.thrift
```

######jconsole remote
```
java -cp case_java8-1.0-SNAPSHOT-jar-with-dependencies.jar  \
-Djava.rmi.server.hostname='192.168.245.150' \
-Dcom.sun.management.jmxremote \
-Dcom.sun.management.jmxremote.port='10086' \
-Dcom.sun.management.jmxremote.ssl=false \
-Dcom.sun.management.jmxremote.authenticate=false \
cn.itcast.test.Test3
```
