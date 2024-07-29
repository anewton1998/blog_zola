+++
title = "Reactive Architectures: Comparing Vert.x to Spring WebFlux"
description = "Reactive Architectures: Comparing Vert.x to Spring WebFlux"
date = "2018-06-05"
tags = [ "Vert.x", "Spring", "WebFlux", "Reactive", "ReactiveX", "Streams", "Rx"]
+++


We've now reached a point in the lifecycle of server-based web application architectures where the hot-stuff that came about during and even the generation after the dot-com bubble is considered "legacy". Application-component containers are no longer necessary; virtualization has moved to a point where we have OS containers. Browsers have reached the point where they are the application, and the need for HTML templating and server-side session state are more trouble than they are worth.

<!-- more -->

And on the backend, where process-per-request gave way to thread-per-request we now have an entirely new shift to "Reactive" programming.

This blog post is my attempt to compare two of these new backend, server architectures in the Java world: Vert.x and Spring WebFlux. I am coming at both of these with no experience in either, a long history of dealing with the legacy application containers (especially JBoss/Wildfly and Tomcat), a need to pick one as the next evolution for the services for which I am responsible.

# Reactive, ReactiveX, and Reactive Streams

A comparison of WebFlux and Vert.x cannot begin without a brief discussion on the topic of Reactive programming, a broad concept and [probably best succinctly described](https://spring.io/blog/2016/06/07/notes-on-reactive-programming-part-i-the-reactive-landscape) as:

> ... a style of micro-architecture involving intelligent routing and consumption of events, all combining to change behaviour.

And discussion of Reactive systems would also be incomplete without a reference to the [Reactive Manifesto](https://www.reactivemanifesto.org/), which I glibly summarize as: software should not suck under load, and it should be message-driven.

ReactiveX (or Reactive Extensions or simply Rx) is a more specific set of APIs and libraries stemming from the work of Jafar Hussain at Microsoft and Ben Christensen at Netflix. Its origins are not Java, and Rx libraries exist for multiple languages. Rx is not just message-driven but an entire set of operating principles around the observer pattern. Their motto is "The Observer Pattern Done Right".

Reactive Streams is a Java-centric API now found in Java 9. Its purpose is to unite the various Reactive libraries available for Java, of which RxJava 2 is one of them. In essence, it is the Java standard for Rx though it is not actually Rx at the API level.

Where Reactive architecture achieves its promise is through a set of operating principles that seek to limit an application to as few threads as possible, hopefully no more than 1 per CPU-core, using non-blocking resources and APIs. By limiting thread count, CPUs make better use of their caches, the OS induces fewer context switches, and the applications need fewer protective locks.

Unlike message-driven architectures of yore, Reactive architecture keeps code more readable via heavy use of functional language features and fluent API programming styles.

# On to Vert.x and Spring WebFlux

From an architecture standpoint, Vert.x is Reactive in that it uses a message-driven architecture and non-blocking modules to keep thread counts low and blocking to a minimum. Its core is a set of event loops, one per thread with a default of one thread per CPU-core. Each event loop passes messages between components. While Reactive, this is neither Rx nor Reactive Streams. As the [Wikipedia entry for Vert.x](https://en.wikipedia.org/wiki/Vert.x) says:

> Similar environments written in other programming languages include [Node.js](https://en.wikipedia.org/wiki/Node.js) for JavaScript, [Twisted](https://en.wikipedia.org/wiki/Twisted_(software)) for Python, [Perl Object Environment](https://en.wikipedia.org/wiki/Perl_Object_Environment) for Perl, [libevent](https://en.wikipedia.org/wiki/Libevent) for C, reactPHP and amphp for PHP and [EventMachine](https://en.wikipedia.org/wiki/EventMachine) for Ruby.

With that said, Vert.x does have [RxJava](https://vertx.io/docs/vertx-rx/java2/) and [Reactive Streams](https://vertx.io/docs/vertx-reactive-streams/java/) integration if so desired. But instead of being at the core, they are placed into individual microservices.

By contrast, WebFlux is based on [Project Reactor](https://projectreactor.io/) which is a Java Reactive Streams implementation. The WebFlux documentation does say that other Reactive libraries may be used, but in reality anybody doing such as thing would be well off the beaten path negating one of the biggest reasons for using WebFlux: the critical mass of the Spring community.

# Microservices

Other than it's core Reactive library, the two differ in their approach to microservices. At the core, a Vert.x component (called a verticle) uses the Vert.x [event bus](https://vertx.io/docs/vertx-core/java/#event_bus):

```java
EventBus eb = vertx.eventBus();

eb.consumer("news.uk.sport", message -> {
  System.out.println("I have received a message: " + message.body());
});
```
Vert.x also encourages passing JSON messages on the event bus. This approach allows for loose-coupling and a system that allows microservices to be written in multiple JVM languages.

By contrast, WebFlux is more centered around offering a Reactive architecture for is `@Controller` model found in Spring MVC. The [Spring documentation](https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html) describes microservice for WebFlux in a much more limited manner:

> In a microservice architecture you can have a mix of applications with either Spring MVC or Spring WebFlux controllers, or with Spring WebFlux functional endpoints.

WebFlux only supports Java and Kotlin (which is 100% integratable with Java), whereas the loose-coupling of Vert.x enables it to support any JVM language.

# Other Protocols

And though not likely to be used be most people, a very interesting difference between WebFlux and Vert.x is the abstraction of the network.

Spring WebFlux, as its name implies, is for Web (HTTP/HTTPS) applications. It uses Netty out of the box, though the documentation does say it can use Tomcat, Undertow, Jetty, etc...

Vert.x, by contrast, seems to be a thicker Swiss Army knife. While it too has built-in Netty support, there is also good support for custom [TCP](https://vertx.io/docs/vertx-core/java/#_writing_tcp_servers_and_clients) and [UDP](https://vertx.io/docs/vertx-core/java/#_writing_tcp_servers_and_clients) services, and even [Unix domain sockets](https://vertx.io/docs/vertx-core/java/#_domain_sockets).

# Blocking and Relational Databases

For an astute reader, the idea of nonblocking threads and standard relational (i.e. SQL) databases probably seem to be at odds, and any shop with a relational database at its core will need an answer for working with it in a Reactive system. It is possible with both WebFlux and Vert.x to use a [non-blocking JDBC driver](https://github.com/mauricio/postgresql-async) with certain databases. But if the database isn't supported or the "experimental" nature of the driver does not provide the necessary level of confidence, then another solution must be found.

And this is where WebFlux and Vert.x really differ.

Here, Spring [discourages the use of WebFlux](https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html):

> If you have blocking persistence APIs (JPA, JDBC), or networking APIs to use, then Spring MVC is the best choice for common architectures at least.

In Vert.x, there are a number of solutions:

1. The Vert.x [JDBC Module](https://vertx.io/docs/vertx-jdbc-client/java/), which is an asynchronous API wrapper around JDBC.
2. The `executeBlocking` call in Vert.x Core.
3. Using a completely separate Verticle called a [Worker Verticle](https://vertx.io/docs/vertx-core/java/#worker_verticles) which runs in a defined set of thread pools.

Non are wonderful, but as the Vert.x documentation on the subject states, "the real world is not like that".

The long-term solution for non-blocking JDBC is the [Asynchronous Database Access API](https://blogs.oracle.com/java/jdbc-next:-a-new-asynchronous-api-for-connecting-to-a-database) (ADBA). But that is probably a few years off, so at present compromise solutions are needed.

# Conclusion

From what I have gathered, Spring WebFlux is mostly geared toward projects that already have an investment in Spring MVC and other Spring technologies but need a Reactive solution.

If, however, your project has no such investment or needs a bit of flexibility beyound a typical web application, Vert.x is probably a better choice.
