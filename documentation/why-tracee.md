---
layout: docs
title: Why TracEE?
category: docs

order: 5
---

In production, logs are still the most reliable source of information which can be used to analyze your applications behavior.
In times of microservices and service oriented architecture analyzing of logs is getting more and more complex.

Log servers like Graylog or the ELK stack are helping you to manage your logs to search the log files for interesting information by offering a simple user interface.

But there's one thing that the log servers can't help you with - they can't aggregate the log information that belongs together on their own. 

This is where TracEE kicks in. It offers bindings for most popular Java frameworks, that will automatically generate tracking information like invocation or session ID's and writes them to your applications log framework contexts.
Another thing TracEE does is to support passing those invocation and session id between all of your components in your application environment, empowering you to gather all log statements that belong to a single invocation or session.

If you are using TracEE, time needed for analyzing your systems behavior - for example in case of an error -  will be drastically reduced. 

Integration of TracEE in your application is very easy and done with almost no effort. 

Please check the <a href="/documentation/getting-started.html">Getting Started</a>, <a href="/backends/slf4j.html">Backend</a> and <a href="http://localhost:4000/bindings/servlet.html">Binding</a> sections for further details about integration TracEE into your application. 

