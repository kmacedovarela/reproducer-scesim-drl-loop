Issue Reproducer
=======================

Issue: when running a test scenario which triggers a drl rule that goes into infinite loop, business central UI becomes unusable. As the rule inserts new facts on the memory, the server ends up with out of memory exception.

How to reproduce:
1. Import the project to business central
2. Click on "Test", or, open the test scenario and run the tests.

Exception:

```
08:54:57,647 INFO  [org.drools.compiler.kie.builder.impl.KieContainerImpl] (default task-15) Start creation of KieBase: defaultKieBase
08:54:57,705 INFO  [org.drools.compiler.kie.builder.impl.KieContainerImpl] (default task-15) End creation of KieBase: defaultKieBase

Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "activemq-failure-check-thread"

Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "default I/O-18"

Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "default Accept"

Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "ExecutorPoolWorker"

Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "Timer-1"

Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "Periodic Recovery"`
Exception: java.lang.OutOfMemoryError thrown from the UncaughtExceptionHandler in thread "Thread-153"

08:58:02,002 ERROR [stderr] (pool-37-thread-1) Exception in thread "pool-37-thread-1" Exception in thread "Thread-0 (-scheduled-threads)" Exception in thread "ServerService Thread Pool -- 41" Exception in thread "ServerService Thread Pool -- 1" Exception in thread "ServerService Thread Pool -- 82" Exception in thread "sshd-SshServer[3bd1d3db](port=8001)-timer-thread-1" Exception in thread "Thread-122" Exception in thread "Thread-4 (ActiveMQ-scheduled-threads)" Exception in thread "FileSystemWatcher" Exception in thread "Thread-17 (ActiveMQ-server-org.apache.activemq.artemis.core.server.impl.ActiveMQServerImpl$6@24ed2a30)" Exception in thread "mysql-cj-abandoned-connection-cleanup" Exception in thread "default task-16" Exception in thread "RxSchedulerPurge-1" Exception in thread "Thread-7 (ActiveMQ-server-org.apache.activemq.artemis.core.server.impl.ActiveMQServerImpl$6@24ed2a30)" java.lang.OutOfMemoryError: Java heap space
08:58:02,059 ERROR [stderr] (Thread-7 (ActiveMQ-server-org.apache.activemq.artemis.core.server.impl.ActiveMQServerImpl$6@24ed2a30)) java.lang.OutOfMemoryError: Java heap space
08:58:02,068 ERROR [stderr] (RxSchedulerPurge-1) java.lang.OutOfMemoryError: Java heap space
08:58:02,069 ERROR [stderr] (default task-16) java.lang.OutOfMemoryError: Java heap space
08:58:02,069 ERROR [stderr] (ServerService Thread Pool -- 1) java.lang.OutOfMemoryError: Java heap space
08:58:02,069 ERROR [stderr] (mysql-cj-abandoned-connection-cleanup) java.lang.OutOfMemoryError: Java heap space
08:58:02,069 ERROR [stderr] (Thread-17 (ActiveMQ-server-org.apache.activemq.artemis.core.server.impl.ActiveMQServerImpl$6@24ed2a30)) java.lang.OutOfMemoryError: Java heap space
08:58:02,070 ERROR [stderr] (Thread-0 (-scheduled-threads)) java.lang.OutOfMemoryError: Java heap space
08:58:02,070 ERROR [stderr] (FileSystemWatcher) java.lang.OutOfMemoryError: Java heap space
08:58:02,070 ERROR [stderr] (Thread-4 (ActiveMQ-scheduled-threads)) java.lang.OutOfMemoryError: Java heap space
08:58:02,070 ERROR [stderr] (Thread-122) java.lang.OutOfMemoryError: Java heap space
08:58:02,070 ERROR [stderr] (ServerService Thread Pool -- 82) java.lang.OutOfMemoryError: Java heap space: failed reallocation of scalar replaced objects
08:58:02,071 ERROR [stderr] (sshd-SshServer[3bd1d3db](port=8001)-timer-thread-1) java.lang.OutOfMemoryError: Java heap space
08:58:02,072 ERROR [stderr] (ServerService Thread Pool -- 41) java.lang.OutOfMemoryError: Java heap space`
```
