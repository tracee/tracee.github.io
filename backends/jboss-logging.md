---
title: TracEE backend for JBoss Logging
category: backends
layout: backend
menu_name: JBoss Logging
toc:
order: 40
---
> Backend implementation for jboss-logging 3+

## Installation / Usage

You need exactly one backend provider on your runtime classpath. Add following to your `pom.xml` to add this module to your dependency tree:

```xml
<dependencies>
...
	<dependency>
		<groupId>io.tracee.backend</groupId>
		<artifactId>tracee-jboss-logging</artifactId>
		<version>RELEASE</version> <!-- You should specify a version instead -->
		<scope>runtime</scope>
	</dependency>
...
</dependencies>
```
