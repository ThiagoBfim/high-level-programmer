# Distributed System with Spring Cloud



I will show some patterns to use with distributed systems and cloud applications.

All the examples shown below can be found on the [Github - Project](https://github.com/ThiagoBfim/spring-cloud-sample).

The Spring Cloud provides tools for developers to quickly build some of the common patterns in distributed systems (e.g. configuration management, service discovery, circuit breakers, intelligent routing, micro-proxy, control bus, one-time tokens, global locks, leadership election, distributed sessions, cluster state).

In this article, we are going to talk about just a few of them.

### Monitoring (Actuator)

Actuator is mainly used to expose operational information about the running application — health, metrics, info, dump, env, etc.

In Kubernetes, the Liveness and Readiness Kubernetes concepts represent facets of the application state.

The Liveness state of an application tells whether the internal state is valid. The Kubernetes uses liveness probes to know when to restart a container.

The Readiness state tells whether the application is ready to accept client requests.

**Properties:**

```
management:
  health:
    circuitbreakers:
      enabled: true
  endpoints:
    web:
      exposure:
        include: health
  endpoint:
    health:
      show-details: always
```

We can configure the actuator to show information about the circuit breaker as shown above.

We are exposing the health path, with that access two URLs:

http://localhost:8080/actuator/health/liveness\
http://localhost:8080/actuator/health/readiness

**Dependencies:**

```

<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
</dependencies>
```

### Circuit Breaker (Resilience4J)

There are many options of CircuitBreaker, for example: Spring Retry, Resilience4J...

We will use the Resilience4J.

_Circuit Breaker:_ Handle faults that may take a variable amount of time to rectify when connecting to a remote service or resource. This pattern can improve the stability and resiliency of an application.

_The Circuit Breaker contains 3 states:_

1. **Closed:** The request from the application is routed through to the operation. If the number of failures is equal than the configured in some space of time, the circuit will be Open.
2. **Open**_:_ The request from the application fails immediately and an exception is returned to the application.
3. **Half-Open:** A limited number of requests from the application are allowed to pass through and invoke the operation. If these requests are successful, it is assumed that the fault that was previously causing the failure has been fixed and the circuit breaker switches to the Closed state (the failure counter is reset).

**Code:**

```
@CircuitBreaker(name = "blogSearch", fallbackMethod = "fallback")
public Object callMethod(String param) { ... }


public Object fallback(String param, Exception exception) { ... }
```

**Properties:**

```
resilience4j:
  circuitbreaker:
    instances:
      blogSearch:
        registerHealthIndicator: true
        eventConsumerBufferSize: 10
        failureRateThreshold: 50
        minimumNumberOfCalls: 5
        automaticTransitionFromOpenToHalfOpenEnabled: true
        waitDurationInOpenState: 5s
        permittedNumberOfCallsInHalfOpenState: 3
        slidingWindowSize: 10
        slidingWindowType: COUNT_BASED
```

**Dependencies:**

```
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-circuitbreaker-resilience4j</artifactId>
</dependency>
```

### Retry (Resilience4J)

_Retry:_ Enable an application to handle temporary failures when connecting to a service or network resource by transparently retrying the operation in the expectation that the failure is transient. This pattern can improve the stability of the application

**Code:**

```
@Retry(name = "blogSearch", fallbackMethod = "fallback")
public Object callMethod(String param) { ... }


public Object fallback(String param, Exception exception) { ... }
```

**Properties:**

```
resilience4j:
  retry:
    instances:
      blogSearch:
        maxAttempts: 5
        waitDuration: 1s
```

**Dependencies:**

```
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-circuitbreaker-resilience4j</artifactId>
</dependency>
```

### Rate Limiting (Resilience4J)

There are many options for Rate Limiting, for example: Bucket4j, Spring Cloud Gateway, Resilience4J...

We will continue with Resilience4J as it provides many features as we saw above.

_Rate limiting_ is a technique to control the rate by which an API or a service is consumed. In a distributed system, no better option exists than to centralize configuring and managing the rate at which consumers can interact with APIs. Only those requests within a defined rate would make it to the API. Anymore would raise an HTTP “Many requests” error.

**Code:**

```

@RateLimiter(name = "blogSearch")
public Object callMethod() { ... }
```

**Properties:**

```
resilience4j:
  ratelimiter:
    instances:
      blogSearch:
        registerHealthIndicator: true
        limitForPeriod: 10
        limitRefreshPeriod: 10s
        timeoutDuration: 3s
```

**Dependencies:**

```
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-circuitbreaker-resilience4j</artifactId>
</dependency>
```

### Service Discovery (Spring Cloud Kubernetes)

Spring Cloud Kubernetes provides implementations of well known Spring Cloud interfaces allowing developers to build and run Spring Cloud applications on Kubernetes.

This project provides an implementation of Discovery Client for Kubernetes. This client lets you query Kubernetes endpoints (see services) by name. A service is typically exposed by the Kubernetes API server as a collection of endpoints that represent HTTP and HTTPS addresses and that a client can access from a Spring Boot application running as a pod.

**Code:**

```
@SpringBootApplication
@EnableDiscoveryClient
@EnableScheduling
public class SpringAdminApplication { ...}
```

You will need these 2 annotations (@EnableDiscoveryClient and @EnableScheduling).

Spring Cloud Kubernetes can also watch the Kubernetes service catalog for changes and update the DiscoveryClient implementation accordingly. In order to enable this functionality, you need to add @EnableScheduling on a configuration class in your application.

**Properties:**

```
cloud:
  kubernetes:
    discovery:
      all-namespaces: true
      service-labels:
        spring-boot: true
```

With service-labels property, we are saying that we want to look just for the services that contain that label.

**Dependencies:**

```
</dependencies>
...

  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-kubernetes</artifactId>
    <version>1.1.0.RELEASE</version>
  </dependency>

...
</dependencies>

<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework.cloud</groupId>
      <artifactId>spring-cloud-dependencies</artifactId>
      <version>${spring-cloud.version}</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>
```

Look in the documentation for the latest versions.

### REST Client (OpenFeign)

_Feign_ is a declarative web service client. It makes writing web service clients easier. To use Feign create an interface and annotate it.

It is very common to need to communicate with some API within our service, Feign is a good web service client to handle this.

### Conclusion

Spring Cloud provides a lot of things that help the developers to work with distributed systems.

Distributed systems are not easy, and there are many others patterns to know, but this is a good beginning.

If you want to learn more, read this book from Microsoft [Cloud Design Patterns: PRESCRIPTIVE ARCHITECTURE GUIDANCE FOR CLOUD APPLICATIONS](https://download.microsoft.com/download/b/b/6/bb69622c-ab5d-4d5f-9a12-b81b952c1169/clouddesignpatternsbook-pdf.pdf)

### References

* [Liveness and Readiness Probes with Spring Boot](https://spring.io/blog/2020/03/25/liveness-and-readiness-probes-with-spring-boot)
* [Kubernetes - Configure Liveness, Readiness and Startup Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)
* [Spring Boot Actuator](https://www.baeldung.com/spring-boot-actuators)
* [Resilience4J](https://resilience4j.readme.io/docs/getting-started-3)
* [Spring Cloud Circuit Breaker](https://spring.io/projects/spring-cloud-circuitbreaker)
* [Spring Cloud Kubernetes](https://spring.io/projects/spring-cloud-kubernetes)
* [Spring Cloud Sample - Github](https://github.com/ThiagoBfim/spring-cloud-sample)
* [API Rate Limiting with Spring Cloud Gateway](https://spring.io/blog/2021/04/05/api-rate-limiting-with-spring-cloud-gateway)
* [Spring Cloud OpenFeign](https://cloud.spring.io/spring-cloud-openfeign/reference/html/)
