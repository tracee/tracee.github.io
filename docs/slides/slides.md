Monitoring distributed Java enterprise applications is __hard__.

<!-- click -->

You have: A bunch of log files on many™ machines.

You hopefully have: A central place where you aggregate your logs.

Each log statement has a logging-context.

<!-- click -->

### What is a logging context?

> Information that you see in log files beside the actual log message

Such as _time_, _thread-name_, _log-level_ ...

```ini
2014-02-11 15:35:04.127 [ajp-bio-8009-exec-9] ERROR freemarker.runtime -
  Error executing FreeMarker template
```
<!-- click -->

### Is a logging context useful?

Yes!

* Time gives your log a chronological order
* Thread-Name allow you to (locally) group logs by _system interactions_

<!-- click -->

### Limitations

* This does not work with asynchronous processing (JMS, servlet-async).
* This does not work over system borders.

<!-- click -->

Example:
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

Which User caused the error?

We lost our _system interaction_ context!

<!-- click -->

### How does TracEE fit in?

* TracEE __emits__ additional context data (requestId, sessionId)
* TracEE __transmits__ the logging context over system borders

<!-- click -->

### TracEE in action

Example again:

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

<!-- click -->

### Profit!

* Logs can be filtered by system interactions or even user sessions!
* Exception causing system interactions can now be traced back to their initial request!

<!-- click -->

### 5 MINUTES OVER


# THANKS

### BY Daniel Wegener, Tobias Gindler / [holisticon.de](https://www.holisticon.de)

But: There is more...