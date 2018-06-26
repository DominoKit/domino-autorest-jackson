# domino-autorest-jackson

The aim of this project is to integrate [gwt-jackson-apt](https://github.com/DominoKit/gwt-jackson-apt) with [autorest](https://github.com/intendia-oss/autorest).

#### How to use:

* First add the dependency for *domino-autorest-jackson*
```xml
<dependency>
    <groupId>org.dominokit</groupId>
    <artifactId>domino-autorest-jackson</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>org.dominokit</groupId>
    <artifactId>autorest-jackson</artifactId>
    <version>1.0-SNAPSHOT</version>
    <classifier>sources</classifier>
</dependency>
```

* Add snapshots repository in your pom.xml
```xml
<repositories>
    <repository>
        <id>sonatype-snapshots-repo</id>
        <url>https://oss.sonatype.org/content/repositories/snapshots</url>
        <snapshots>
            <enabled>true</enabled>
            <updatePolicy>always</updatePolicy>
            <checksumPolicy>fail</checksumPolicy>
        </snapshots>
    </repository>
</repositories>
```

* Add *jackson-apt-processor* dependency
```xml
<dependency>
    <groupId>org.dominokit.jacksonapt</groupId>
    <artifactId>jackson-apt-processor</artifactId>
    <version>1.0-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

* Add the module in your **.gwt.xml*
```xml
<inherits name="org.dominokit.autorest.jackson.JacksonAutoRest"/>
```

* Define package-info.java file and annotate it with `@JSONRegistration` annotation passing your module name:
```java
@JSONRegistration("Foo")
package com.foo;

import org.dominokit.jacksonapt.annotation.JSONRegistration;
```

* Use `JacksonResourceBuilder` and pass it the generated registry as follows:

```java
new JacksonResourceBuilder(new FooJsonRegistry());
```
