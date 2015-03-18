---
title: TracEE binding for Apache HttpClient 3.x
category: bindings
layout: binding
menu_name: HttpClient
toc:

---

TODO Wrapper for [Apache HttpClient 3](http://hc.apache.org/httpclient-3.x/)

## Installation

Add the `tracee-httpclient` module to your `pom.xml` dependencies:

```xml
<dependencies>
...
    <dependency>
        <groupId>io.tracee.binding</groupId>
   		<artifactId>tracee-httpclient</artifactId>
        <version>RELEASE</version>
    </dependency>
...
</dependencies>
```

Then simply replace the pure instantiation of the HttpClient in your code with:

```java
final HttpClient client = new HttpClient();
```

with the `TraceeHttpClientDecorator`:

```java
final HttpClient client = TraceeHttpClientDecorator.wrap(new HttpClient());
```
