---
title: TracEE bindings
category: bindings
layout: docs
menu_name: Overview
toc:
order: 0
---

The following tables gives an overview over all frameworks and libraries that are supported by TracEE on the inbound and outbound side.

> Sometimes there are different ways to integrate TracEE into your application because some of these frameworks are built on top of each other (like JAX-RS is based on Servlets and Spring Web is based on HttpComponents). We recommend to use the most specific binding. The following tables is sorted from specific to more generic frameworks. You normally should pick the first entry that matches your need.

## Inbound Bindings

| Framework | Binding |
| ---------------------------:|:---------|
| Spring MVC                  | Use [tracee-springmvc](springmvc.html)'s `TraceeInterceptor`. |
| Spring Web <br>(Rest-Clients)   | Use [tracee-springhttpclient](springhttpclient.html)'s `TraceeClientHttpRequestInterceptor`. |
| Spring Web Services         | Add [tracee-springws](springws.html)'s `TraceeEndpointInterceptor`. |
| JAX-RS2                     | Use [tracee-jaxrs2](jaxrs2/)'s `TraceeContainerRequestFilter` and `TraceeContainerResponseFilter`. |
| JAX-RS                      | Use [tracee-servlet](servlet.html) as a servlet filter. |
| JAX-WS                      | Use [tracee-jaxws](jax-ws.html)'s `TraceeHandlerChain.xml` as `@HandlerChain`. |
| Servlet                     | Use [tracee-servlet](servlet.html) as a servlet filter. |
| JMS                         | MDB: Use [trace-jms](jms.html)'s `TraceeMessageListener` as EJB interceptor. |
| Apache CXF                  | Use [tracee-cxf](cxf.html)'s `TraceeCxfFeature` |
| Quartz Scheduler            | Use [tracee-quartz](quartz.html)'s `TraceeJobListener` to generate context before the job starts |

## Outbound Bindings

| Framework | Binding |
| ---------------------------:|:---------|
| Spring Web (Rest-Clients)   | Use [tracee-springhttpclient](springhttpclient.html)'s `TraceeClientHttpRequestInterceptor`. |
| JAX-RS                      | Configure [tracee-httpclient](httpclient.html) as Executor |
| JAX-RS2                     | Configure [tracee-jaxrs2](jaxrs2/)'s `TraceeClientRequestFilter` and `TraceeClientResponseFilter` |
| JAX-WS                      | Use [tracee-jaxws](jax-ws.html)'s `TraceeClientHandlerResolver` |
| JMS                         | Producer: Use [tracee-jms](jms.html)'s `TraceeMessageWriter.wrap` on your `MessageWriter` |
| Apache CXF                  | Use [tracee-cxf](cxf.html)'s `TraceeCxfFeature` |
| Apache HttpComponents (4.x) | Use [tracee-components](httpcomponents.html)'s `TraceeHttpRequestInterceptor` and `TraceeHttpResponseInterceptor` |
| Apache HttpClient (3.x)     | Use [tracee-httpclient](httpclient.html)'s `TraceeHttpClientDecorator` |
