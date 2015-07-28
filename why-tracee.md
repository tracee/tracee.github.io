---
layout: docs
menu_name: Why TracEE?
title: Why TracEE?
order: 2
---

In production, logs are still the most reliable source of information which can be used to analyze your application's behavior.
In times of microservices and service oriented architecture analyzing of logs is getting more and more complex.

Log servers like Graylog or the Elasticsearch, Logstash, Kibana (ELK) stack help you to manage your logs and search the log files for interesting information by offering a simple unified user interface.

But there is one thing that the log servers can't help you with - they can't aggregate the log information that belong together on their own.

```ini
2014-02-11 15:35:04.127 [tomcat-exec-1] INFO
  my.business.webapp.Servlet - Calling the backend for user Alice now!
2014-02-11 15:35:04.128 [tomcat-exec-2] INFO
  my.business.webapp.Servlet - Calling the backend for user Bob now!
2014-02-11 15:35:05.999 [jboss-exec-15] INFO
  my.business.backend.Service - Everything went fine!
2014-02-11 15:35:05.999 [jboss-exec-21] WARN
  my.business.backend.Service - Something went terribly wrong!
```

This is where TracEE kicks in. It offers bindings for most popular Java frameworks, that will automatically generate tracking information like invocation or session ids and writes it to your applications log framework contexts. The idea is pretty similar to correlation ids that you manually put into your application APIs to make sense of system interactions - but TracEE solves this for you - automatic and transparent!

Another thing TracEE does is to support passing those ids between all of your components in your application environment, empowering you to gather all log statements that belong to a single invocation, session or other kind of correlation.

Thus using TracEE drastically reduces the time needed for analyzing your systems behavior - for instance in case of an error. 

```ini
2014-02-11 15:35:04.127 [rxId:BABO sessionId:AFF3] [tomcat-exec-1] INFO
  my.business.webapp.Servlet - Calling the backend for user Alice now!
2014-02-11 15:35:04.128 [rxId:BABA sessionId:EEEE] [tomcat-exec-2] INFO
  my.business.webapp.Servlet - Calling the backend for user Bob now!
2014-02-11 15:35:05.999 [rxId:BABA sessionId:EEEE] [jboss-exec-15] INFO
  my.business.backend.Service - Everything went fine!
2014-02-11 15:35:05.999 [rxId:BABO sessionId:AFF3] [jboss-exec-21] WARN
  my.business.backend.Service - Something went terribly wrong!
```

The integration of TracEE into your application is very easy and doable with almost no effort but adding the TracEE dependencies.

Read the [Getting Started](/documentation/getting-started.html) and [Bindings](http://localhost:4000/bindings/servlet.html) sections for further details about integrating TracEE into your application.

