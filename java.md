###### convert .class to .java

```shell
[root@127.0.0.1 ~]$ cd ../WEB-INF/classes/com/sample/service/impl
[root@127.0.0.1 impl]$ javap -c MyServiceImpl
```

###### mvn generate

```shell
mvn archetype:generate -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.sample -DartifactId=sample-common -Dversion=1.0-SNAPSHOT -Dpackage=com.sample.thrift
```

