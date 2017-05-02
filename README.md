# Riptide

Riptide is a super-simple multiplatform messaging-bus with built-in
- Thread-safe dispatch so you don't have to worry about concurrency
- Message correlation so your related messages can be handled together
- Multi platform implementations so you can have polyglot components
- Easy to use API which hides the complexity of message passing

Check the Wiki [here][mavenlink].

__Note that__ this guide details the usage of the reference implementation which is written in *Kotlin* and can be used by any JVM language capable of Java interop.

## Getting started

- Grab a copy of Riptide using either Maven:

      <dependency>
          <groupId>org.codetome.riptide</groupId>
          <artifactId>riptide.core.java</artifactId>
          <version>2017.1.0</version>
      </dependency>
  or Gradle:
      
      compile group: 'org.codetome.riptide', name: 'riptide.core.java', version: '2017.1.0'

- Configure and create the `RiptideService`:

      RiptideService rs = new RiptideServiceBuilder()
          .useRabbit(new RabbitConfig("localhost", 5672))
          // this optional switch makes all correlated messages dispatch on a single thread but concurrently with non-related messages
          // useful when you don't want to handle race conditions with your related messages and want them to be processed serially
          .dispatchProcessesOnSingleThread()
          .build();
       





[mavenlink]:https://github.com/Riptide/riptide.docs/wiki
