# autorest-jackson

Use:
```java
<dependency>
    <groupId>org.dominokit</groupId>
    <artifactId>autorest-jackson</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>org.dominokit</groupId>
    <artifactId>autorest-jackson</artifactId>
    <version>1.0-SNAPSHOT</version>
    <classifier>sources</classifier>
</dependency>
```

Add the jackson-registration-apt dependency:
```java
<dependency>
    <groupId>org.dominokit.jacksonapt</groupId>
    <artifactId>jackson-registration-apt</artifactId>
    <version>1.0-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

and make sure that jackson-apt-processor
```java
<dependency>
    <groupId>org.dominokit.jacksonapt</groupId>
    <artifactId>jackson-apt-processor</artifactId>
    <version>1.0-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

Add the module in your *.gwt.xml
`<inherits name="org.dominokit.autorest.jackson.JacksonAutoRest"/>`

All you need to do is to create package-info.java file and annotate it with `@JSONRegistration` annotation passing your module name:
```java
@JSONRegistration("Foo")
package com.foo;

import org.dominokit.jacksonapt.annotation.JSONRegistration;
```

and then use it as follows:

```java
new JacksonResourceBuilder(new FooJsonRegistry());
```
