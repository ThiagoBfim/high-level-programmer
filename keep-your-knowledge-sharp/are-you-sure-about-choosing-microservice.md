# Are you sure about choosing Microservice?

Before we get started, remember that the microservice is an architectural pattern; like all patterns, there is a better case for using it, we will talk more about that :)

### Microservice vs Monolith

A monolithic architecture is a singular, large computing network with one code base that couples all the business concerns together.

The microservice architecture enables the rapid, frequent and reliable delivery of large, complex applications. It also enables an organization to evolve its technology stack.

### When to use microservice?

Microservice is usually better when you have more people working on the product. Microservice have more things to deal with than the Monolith, but also have some advantages.

* In big teams, when there are many people, so it's possible to divide the teams into separate services.
* With a big application, probably there will be easier to find and fix a bug in a small service than in a big monolith.
* It's easier to scale, with microservice you can scale individually.
* Reliability is easier to deal with, each microservice must work independently, so if there is a bug in one microservice, it shouldn't affect the others.

### When should I not use microservice?

Microservice is not a silver bullet. There are some cases where you probably will not need to use microservice architecture, but like everything in IT, it depends :)

* Small teams, if you have a small team, probably just one code base will be easier to deal with.
* If you don't need to scale just a few services.
* Need to deliver a product fast, like an MVP (Minimum Viable Product)
* Don't have a strong CI/CD well-defined, and a DevOps team to help with it.

### Advantages vs Disadvantages

Like everything in the world, there are trade-offs. Microservice is the same, there are pros and cons.

I'll show just a few of them here, of course, there are more, and it depends on each case.

#### Advantages

Microservice is easier when you need to break the software into small pieces that are independent.

* Scalability - With microservice you can scale just a single service, that requires more instances.
* Isolation - One of the cores of microservice is to be independent, and with that, we have the Isolation
* Flexibility - It's possible to use different types of technologies.
* Independently deployable – Microservices are individual units, and autonomous, so they allow for fast and easy independent deployment, with few chances to cause system failures.
* High reliability – You can deploy changes for a specific service, without the threat of bringing down the entire application.

#### Disadvantages

Microservice architecture is more complex. If you choose to use this architecture you should also deal with:

* DevOps in the beginning - You will need a good CI/CD in the beginning, otherwise it will become a big problem, and each microservice will have a new cost for the CI/CD pipeline.
* Debugging - It's harder to monitor and figure out where the problem is.
* E2E Test - Hard to Test, it is hard to create an E2E test with many microservices.
* Eventual consistency - Maintaining strong consistency is extremely difficult for a distributed system.
* Refactoring - It's hard to refactor functionality between services

<figure><img src="../.gitbook/assets/productivity.png" alt=""><figcaption><p>https://martinfowler.com/bliki/MicroservicePremium.html</p></figcaption></figure>

### CI/CD

If you will work with Microservice you will need to know more about CI/CD, and pipelines.

It's crucial to have a good CI/CD, because it's impossible to deal with 100 microservice deployments manually.

The pipeline is the steps that your software will do to complete the deployment gracefully. Your pipeline should be able to check if the code is working fine, and if is able to deploy in different environments. It also should be able to do the deployment in different environments, automatically or manually.

#### CI: Continuous Integration

In the CI your pipeline should do things like this:

* Run some lint code, check for code-style, for example, Sonar.
* Run the tests, and guarantee that the software will not break in production. Here you can also check for coverage.
* Run security checks, there are different types of checks that can be done in this step. Tools like Horusec, Snyk, and Sonar can help in this step.

#### CD: Continuous delivery/deployment

In the CD step, you should be able to deliver a new version of the application.

* Build the application
* Create a tag or a new version for this step
* Delivery the new version in the chosen environment
* Ensure that the settings will be in accordance with the chosen environment.
* Be able to roll back if it has any problem.

This is just the beginning, CI/CD is a world, and there are so many things to talk about it.

### Container

To work with Cloud and CI/CD, you probably will need a contained application, it will make your life much easier.

> "A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another"\
> \
> \- Docker

To work with containers there are some options, like docker, podman, containerd...

### Kubernetes and Cloud

You also should know about K8s and Cloud to work well with microservices.

_"Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications."_

_"Cloud computing is the on-demand delivery of IT resources over the Internet with pay-as-you-go pricing"_

K8s and Cloud will help you to deliver and scale your applications easier, and much more.

There are many things to talk about this subject, so just keep in mind that this is important knowledge to have if you will work with microservices.

### Observability

_"Observability is the ability to measure the internal states of a system by examining its outputs. A system is considered “observable” if the current state can be estimated by only using information from outputs, namely sensor data."_

If you are working with microservice Observability is a must thing to have. When you have multiple microservices and you are having any trouble in production you should be able to identify the problem quickly, this is the reason that observability is so important.

_"In an observability scenario, where an environment has been fully instrumented to provide complete observability data, you can flexibly explore what’s going on and quickly figure out the root cause of issues you may not have been able to anticipate."_

There are some tools that may help you with it: Dynatrace, Datadog , Splunk, ElasticSearch Stack.

### Conclusion

Microservice architecture is very useful, but is not a silver bullet.

In the case of choosing to use microservice architecture, you will need to know the things above.

* Container
* Kubernetes
* Cloud
* Observability

And this is just the beginning, distributed systems usually have big challenges :) You have more scalability and high reliability, however, on the other side you have to manage more systems, and ensure they work well together, even if one of them stops working, so be aware of the hard task to maintain the data consistency.

You can search about **chaos engineer**, to know how to test distributed system introduction failures.

You should also know about design patterns for microservice like Saga pattern, Circuit Breaker, and others, to know more about it, you can read this article [Microservices Design Patterns](https://learncsdesign.medium.com/microservices-design-patterns-91fe56a33a47)

### References

* [microservices.io](https://microservices.io/)
* [Pattern: Monolithic Architecture](https://microservices.io/patterns/monolithic.html)
* [Monolith First](https://martinfowler.com/bliki/MonolithFirst.html)
* [Microservices vs. monolithic architecture](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith)
* [Microservices Guide - Martin Fowler](https://martinfowler.com/microservices/)
* [Continuous security testing](https://snyk.io/learn/what-is-ci-cd-pipeline-and-tools-explained/continuous-security/testing/)
* [What Is Observability? - Splunk](https://www.splunk.com/en\_us/data-insider/what-is-observability.html)
* [Data Consistency in Microservices Architecture](https://medium.com/garantibbva-teknoloji/data-consistency-in-microservices-architecture-5c67e0f65256)
