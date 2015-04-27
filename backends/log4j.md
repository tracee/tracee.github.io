---
title: TracEE backend for Apache Log4J
category: backends
layout: backend
menu_name: Log4J
toc:
order: 20
---
> Backend implementation for [log4j (1.2.4+)](http://logging.apache.org/log4j/1.2/)

## Installation

You need exactly one backend provider on your runtime classpath. Add following to your `pom.xml` to add this module to your dependency tree:

```xml
<dependencies>
...
	<dependency>
		<groupId>io.tracee.backend</groupId>
		<artifactId>tracee-log4j</artifactId>
		<version>RELEASE</version> <!-- You should specify a version instead -->
		<scope>runtime</scope>
	</dependency>
...
</dependencies>
```