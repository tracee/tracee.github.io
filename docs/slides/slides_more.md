## TracEE in a nutshell

* _Invents_ invocation context parameters
* Enriches logging (through MDC)
* Transports context to remote systems
* Transports context through asynchronous processing (JMS, Servlet3 async)

<!-- click -->

## What is a context parameter?
###(in terms of TracEE)

* RequestId
* Incoming Http-Paramter
* SessionId (masked)
* CorrelationId from external system
* ConversationId from fat browser app
* SSO-Token

<!-- click -->

To be drawn
![System overview](assets/here_comes_tracee.jpg)

<!-- click -->

## How to use it?

* Configure __Incoming-Interceptors__
    * TraceeFilter (Servlet)
    * or SpringTraceeFilter (Spring Interceptor)
    * or TraceeServerHandler (SOAP)
    * _..._
* Configure __Outgoing-Interceptors__
    * HttpClientPropagator (Apache HttpClient, REST)
    * TraceeClientHandler (SOAP)
    * _..._

<!-- click -->

## How to use it? II

* Configure your logging frameworks
    * Context is accessible from MDC

```xml
<appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
    <layout>
        <Pattern>rqId: %X{requestId} sId: %X{sessionId} - %m%n</Pattern>
    </layout>
</appender>
```

<!-- click -->

## Inside TracEE

* Assertion: JavaEE uses a thread-per-connection model
* Exceptions: AsyncServlet, JMS
* Idea: Storing context in a ThreadLocal
    * Better: Reusing the logging MDC

<!-- click -->

## Inside TracEE II

So what TracEE essentially does:

* Intercepting Incoming Requests and parsing a given Context to the MDC
* Intercepting Outgoing Responses and writing the MDC to the transport
* Intercepting Outgoing Requests and writing the MDC to the transport
* Intercepting Incoming Responses and parsing a given Context to the MDC

* ... something analogous for asynchronous processing

<!-- click -->

## I can haz more?

* Exception-Logging with full protocol specific  (wire HTTP-Requests) invocation parameters
* SessionLifecycleListener stores sessionId in the context as soon as it exists
* SPI: Roll your own Protocol-Adapters

<!-- click -->

## Known limitations

* RemoteEJB cannot be supported by spec. Custom container implementations might work.
* Accumulation of sessions from different frontends might be difficult.

<!-- click -->

# KKTHXBYE

# CONTRIBUTE!