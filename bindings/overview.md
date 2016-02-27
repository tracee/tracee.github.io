---
title: TracEE bindings
category: bindings
layout: docs
menu_name: Overview
toc:
order: 0
---

The following table gives an overview over all frameworks and libraries that are supported by TracEE.

| Framework | Client | Server / Container |
| ---------------------------:|:------:|:---------:|
| Servlet                     | - | Use [tracee-servlet](servlet.html) as a servlet filter. |
| Spring MVC                  | - | Use [tracee-springmvc](springmvc.html)'s `TraceeInterceptor`. |
| Spring Web (Rest-Clients)   | Use [tracee-springhttpclient](springhttpclient.html)'s `TraceeClientHttpRequestInterceptor`. | - |
| Spring Web Services         | Add [tracee-springws](springws.html)'s `TraceeClientInterceptor`. | Add [tracee-springws](springws.html)'s `TraceeEndpointInterceptor`. |
| JAX-RS                      | Configure [tracee-httpclient](httpclient.html) as Executor | Use [tracee-servlet](servlet.html) as a servlet filter. |
| JAX-RS2                     | Configure [tracee-jaxrs2](jaxrs2/)'s `TraceeClientRequestFilter` and `TraceeClientResponseFilter` | Use [tracee-jaxrs2](jaxrs2/)'s `TraceeContainerRequestFilter` and `TraceeContainerResponseFilter`. |
| JAX-WS                      | Use [tracee-jaxws](jax-ws.html)'s `TraceeClientHandlerResolver` | Use [tracee-jaxws](jax-ws.html)'s `TraceeHandlerChain.xml` as `@HandlerChain`. |
| JMS                         | Producer: Use [tracee-jms](jms.html)'s `TraceeMessageWriter.wrap` on your `MessageWriter` | MDB: Use [trace-jms](jms.html)'s `TraceeMessageListener` as EJB interceptor. |
| Apache HttpClient (3.x)          | Use [tracee-httpclient](httpclient.html)'s `TraceeHttpClientDecorator` | - |
| Apache HttpComponents (4.x)          | Use [tracee-components](httpcomponents.html)'s `TraceeHttpRequestInterceptor` and `TraceeHttpResponseInterceptor` | - |
| Apache CXF                  | Use [tracee-cxf](cxf.html)'s `TraceeCxfFeature` | Use [tracee-cxf](cxf.html)'s `TraceeCxfFeature` |
| Quartz Scheduler            | - | Use [tracee-quartz](quartz.html)'s `TraceeJobListener` to generate context before the job starts |