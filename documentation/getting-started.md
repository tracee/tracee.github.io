---
layout: docs
title: Getting Started
category: docs
toc:
order: 10
---

> This article explains how you can easily integrate TracEE into your projects.

## 

The TracEE framework is used to create and pass the _TracEE Propagated Invocation Context_ (short: __TPIC__) information - which for example consists of invocation and session ids - throughout your applications system environment. 

TracEE uses the MDC ( _Mapped Diagnostic Context_ ) of your applications underlying log framework to store the TPIC during the invocation processing in your components. It uses the popular log abstraction slf4j and therefore can be used with most of the popular java logging frameworks like logback, log4j2, log4j and jboss-logging.

You normally only need to [configure slf4j to use your preferred logging framework](http://www.slf4j.org/manual.html#swapping).

## Step 2 : Provide Bindings
TracEE offers technology related binding artifacts which handle the generation or propagation of the TPIC information at the borders of your application or its components - this includes sending, receiving and returning of TPIC information to or from other components.

<img src="/assets/img/docs/gettingStarted_tpic_propagation.svg" />

At the moment TracEE provides bindings for a lot of popular Java (EE) frameworks like Servlets, JAX-WS, JAX-RS, JMS, Spring, Apache CXF.

Integration of TracEE binding artifacts highly depend on their related frameworks, therefore there is no common way for integrating those bindings into applications.
Please take a look at the bindings tab for further information about how to integrate TracEE bindings for specific frameworks.

## Overview on all maven artefacts
<!--- todo: find a way to determine last project version -->
You can find all tracee modules and their recent version in the [maven central repository](https://search.maven.org/#search%7Cga%7C1%7Cg%3Aio.tracee.**%20AND%20(p%3A%22bundle%22%20OR%20p%3A%22jar%22).
