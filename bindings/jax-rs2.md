---
title: TracEE binding for JAX-RS2
category: bindings
layout: binding
menu_name: JAX-RS2
toc:
    - "Container-Configuration"
    - Using JAX-RS 2 client
---

> This module can be used to add TracEE context propagation support to JAX-RS 2 webservices and JAX-RS 2 webservice clients.

Please add the following dependency to enable TracEE JAX-RS 2.x ([JSR 339](http://jcp.org/en/jsr/detail?id=339)) support. For example in maven-style projects add to the pom.xml:

```xml
<dependencies>
<!-- … -->
    <dependency>
        <groupId>io.tracee.binding</groupId>
        <artifactId>tracee-jaxrs2</artifactId>
        <version>RELEASE</version> <!-- You should specify a version instead -->
    </dependency>
<!-- … -->
</dependencies>
```

## Container-Configuration

### Implicit

If you don't use an explicit application config and have the `tracee-jaxrs2` module on your classpath, 
all filters will be automatically applied to your JAX-RS services.

### Explicit Application configuration

If you use an explicit `Application` class, you need to add `TraceeContainerFilter` as provider classes.

Example:

```java
@ApplicationPath("/myApplication")
public class ApplicationConfig extends Application {

    public Set<Class<?>> getClasses() {
        return new HashSet<Class<?>>(Arrays.asList(
        io.tracee.binding.jaxrs2.TraceeContainerFilter.class, …);
    }
}
```

## Using JAX-RS 2 client

You have to register the `TraceeClientFilter` as provider classes when you build your client to enable TracEE 
support for JAX-RS2 clients.


```java
final Client client = ClientBuilder.newClient()
    .register(io.tracee.binding.jaxrs2.TraceeClientFilter.class);
final Response response = client.target(ENDPOINT_URL).request().get();
```
