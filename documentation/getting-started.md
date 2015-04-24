---
layout: docs
title: Getting Started
category: docs
toc:
    - Provide Backend Provider
    - Provide Bindings

---

> This article explains how you can easily integrate TracEE into your projects.

## Step 1 : Select a Backend Provider

TracEE uses the MDC ( _Mapped Diagnostic Context_ ) of your applications log framework to store the TPIC (= _TracEE Propagated Invocation Context_ ) information, like invocation and session ids.
Most of the popular java logging frameworks like slf4j, log4j2, log4j and jboss-logging are supported by TracEE.

You just have to bind a TracEE backend artifact depending on the log framework used in your project.
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
The generation or propagation of the TPIC information will be handled by framework specific TracEE binding artifacts at the borders of your applications.
Those binding artifacts allow TPIC creation and propagation - this includes sending, receiving and returning of TPIC information.

<img src="/assets/img/docs/gettingStarted_tpic_propagation.svg" />

At the moment TracEE provides bindings for a lot of popular Java (EE) frameworks like Servlets, JAX-WS, JAX-RS, JMS, Spring, Apache CXF, ...

Integration of TracEE binding artifacts highly depend on their related frameworks, therefore there's no common way for integrating those bindings into applications.
Please take a look at the bindings tab for further information about how to integrate TracEE bindings for specific frameworks.

