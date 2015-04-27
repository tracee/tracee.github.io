---
layout: docs
title: Getting Started
category: docs
toc:
    - Provide Backend Provider
    - Provide Bindings

---

> This article explains how you can easily integrate TracEE into your projects.

The TracEE framework is used to create and pass the TPIC (= _TracEE Propagated Invocation Context_ ) information - which for example consists of invocation and session ids - throughout your applications system environment. 

TracEE uses the MDC ( _Mapped Diagnostic Context_ ) of your applications underlying log framework to store the TPIC during the invocation processing in your components. It supports most of the popular java logging frameworks like slf4j, log4j2, log4j and jboss-logging.

The technology / framework related TracEE binding providers are used to create the TPIC or to transport it between components. 

## Step 1 : Select a Backend Provider

Just bind the TracEE backend artifact depending on the log framework used in your application / component.

For example in maven-style projects add one of the following dependencies to the pom.xml:

```xml
<dependencies>
    ...
    
    <!-- Add this to use slf4j -->
    <dependency>
        <groupId>io.tracee.backend</groupId>
        <artifactId>tracee-slf4j</artifactId>
        <version>RELEASE</version>
    </dependency>
    
    <!-- Add this to use log4j2 -->
    <dependency>
        <groupId>io.tracee.backend</groupId>
        <artifactId>tracee-log4j2</artifactId>
        <version>RELEASE</version>
    </dependency>
    
    <!-- Add this to use log4j -->
    <dependency>
        <groupId>io.tracee.backend</groupId>
        <artifactId>tracee-log4j</artifactId>
        <version>RELEASE</version>
    </dependency>
    
    <!-- Add this to use jboss logging -->
    <dependency>
        <groupId>io.tracee.backend</groupId>
        <artifactId>tracee-jboss-logging</artifactId>
        <version>RELEASE</version>
    </dependency>
        
    ...
</dependencies>
```

## Step 2 : Provide Bindings
TracEE offers technology related binding artifacts which handle the generation or propagation of the TPIC information at the borders of your application or its components - this includes sending, receiving and returning of TPIC information to or from other components.

<img src="/assets/img/docs/gettingStarted_tpic_propagation.svg" />

At the moment TracEE provides bindings for a lot of popular Java (EE) frameworks like Servlets, JAX-WS, JAX-RS, JMS, Spring, Apache CXF.

Integration of TracEE binding artifacts highly depend on their related frameworks, therefore there's no common way for integrating those bindings into applications.
Please take a look at the bindings tab for further information about how to integrate TracEE bindings for specific frameworks.

