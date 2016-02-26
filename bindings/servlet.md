---
title: TracEE binding for Java Servlets
category: bindings
layout: binding
menu_name: Servlet
toc:
    - Installation
order: 90
---

> tracee-servlet contains Servlet-Listeners and -Filters that allows you to use TracEE Context Propagation with Java Servlets.

 * __TraceeServletRequestListener__: Parses a TracEE-Context from a ServletHttpRequest-Header before a request is processed by a servlet. It also cleans the TraceeBackend when the request processing is finished by the container.
 * __TraceeFilter__: Writes a TracEE-Context back to a ServletHttpResponse-Header.
 * __TraceeSessionListener__: Listens on `Session.create()` and `Session.destroy()` events and creates and deletes the tracee-sessionId from the TracEE-Backend accordingly.

## Installation

Its super-easy for Servlet3+-Containers. Just add tracee-servlet-VERSION.jar to your webapp-classpath (`WEB-INF/lib` or as maven runtime dependency). tracee-servlet contains a [web-fragment.xml](src/main/resources/META-INF/web-fragment.xml) that registers all required filters and event listeners.

If you're use Maven for your dependency management simple add this to your pom:

```xml
<dependencies>
<!-- … -->
    <dependency>
        <groupId>io.tracee.binding</groupId>
        <artifactId>tracee-servlet</artifactId>
        <version>RELEASE</version>
        <scope>runtime</scope>
    </dependency>
<!-- … -->
</dependencies>
```

If you are on a Servlet-Container with servlet-version < 3, you need to register the following filters in your web.xml:

```xml
<!-- … -->
<filter>
    <filter-name>traceeFilter</filter-name>
    <filter-class>io.tracee.binding.servlet.TraceeFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>traceeFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
<listener>
    <listener-class>io.tracee.binding.servlet.TraceeServletRequestListener</listener-class>
</listener>
<listener>
    <listener-class>io.tracee.binding.servlet.TraceeSessionListener</listener-class>
</listener>
<!-- … -->
```
You may change the `filter-mapping:url-pattern` according to your needs.

### Spring Boot

If you're running in an embedded SpringBoot container you've to add the ServletListener and Filter to your application configuration:

```java
@Bean
public FilterRegistrationBean traceeFilter() {
    FilterRegistrationBean frb = new FilterRegistrationBean();
    frb.setFilter(new TraceeFilter());
    frb.addUrlPatterns("/*");
    return frb;
}

@Bean
public ServletListenerRegistrationBean traceeServletListener() {
    return new ServletListenerRegistrationBean<TraceeServletRequestListener>(new TraceeServletRequestListener());
}
```
