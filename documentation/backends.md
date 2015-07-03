---
title: TracEE backend for SLF4J / Logback
category: docs
layout: docs
menu_name: Backends
toc:
order: 10
---

> Backend implementation for [slf4j (1.6.6+)](http://www.slf4j.org/)

## Installation

`TODO: ALREADY IN CORE!!!`


## Thread Local Backend

You need exactly one backend provider on your runtime classpath. Add following to your `pom.xml` to add this module to your dependency tree: 

```xml
<dependencies>
...
	<dependency>
		<groupId>io.tracee.backend</groupId>
		<artifactId>tracee-threadlocal-store</artifactId>
		<version>RELEASE</version> <!-- You should specify a version instead -->
		<scope>runtime</scope>
	</dependency>
...
</dependencies>
```
