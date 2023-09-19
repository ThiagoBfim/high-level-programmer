# 7 Things you should know about Java besides the code



Java, a software platform and computer programming language, is one of the most pervasive technologies in the modern world.

Java was originally developed and supported by Sun Microsystems and is now supported by Oracle.

### Java is OOP

Object-Oriented Programming is one paradigm of programming language. This paradigm tries to solve problems based on objects.

There are 4 major pillars in the OOP:

* Abstraction
* Encapsulation
* Inheritance
* Polymorphism

These pillars and OOP concepts help the developer create great software by avoiding duplicate code and allowing you to create cohesive and loosely coupled code.

### Java is over 25 years old

The project was born in 1991, behind the scenes of a Sun Microsystems team, when three engineers, James Gosling, Mike Sheridan, and Patrick Naughton. The small team of sun engineers is called Green Team.

It was James Gosling, one of the members of the Green Project, who originated this new language, which he called Oak.

Then, in 1995, the project was renamed to Java, in honor of the programmer's favorite drink, namely coffee, part of the production of which comes from the island of Java.

### Java is OpenSource

Oracle has a deep commitment to open source and a large and vibrant Java community. To understand how the Java community evolved to where it is today, you need to go back in time.

By the late 1990s and early 2000s, a group of companies, including Sun, realized sharing Java code would be helpful. No individual vendor could fulfill Java’s “write once, run anywhere” mission. “No one vendor can write all of the everywheres, right?” Smith says.

Sun delivered OpenJDK 6, the first open source version of Java, in 2007. OpenJDK 6 was incomplete, but it allowed Sun to begin finding efficient ways of collaborating with other interested parties in an open source process and to begin building the Java open source community.

Another open source breakthrough for Java was in 2017, when Oracle announced plans to ship its own OpenJDK implementation. That was the same year that Oracle transitioned to a six-month release cadence for new versions of Java.

Since September 2021, Oracle provides the Oracle JDK for Java 17 and later under a free use license for All Users.

### Java LTS Program

The LTS version is the Long-Term-Support, so they have more support than the others.

Since Java 17, the release program has been 2 new releases every year, one in March and one in September, and the interval between LTS versions is now two years instead of three.

Oracle proposes to shift the cadence of JDK LTS releases from every three years to every two years.

TIf accepted, this means that the next JDK LTS release after JDK 17 will JDK 21, rather than JDK 23.

The duration of the Oracle JDK LTS support remains unchanged, starting at a minimum of eight years for each LTS release.

### JVM (Java Virtual Machine)

All Java applications run into a JVM. The main() is the starting point for JVM to start the execution of a Java program. Without the main() method, JVM will not execute the program.

The Java Virtual Machine is the cornerstone of the Java platform. It is the component of the technology responsible for its hardware- and operating system-independence, the small size of its compiled code, and its ability to protect users from malicious programs.

The Java Virtual Machine is an abstract computing machine, and there is more than one JVM:

* Eclipse OpenJ9 – open-source from IBM J9, for Windows, AIX, Linux (x86, Power, and Z), macOS, MVS, OS/400, Pocket PC, z/OS.
* GraalVM – is based on HotSpot/OpenJDK, it has a polyglot feature, to transparently mix and match supported languages.
* OpenJDK – is a free and open-source implementation of the Java Platform, Standard Edition (Java SE)

### Garbage collector

One strength of the Java SE platform is that it shields the developer from the complexity of memory allocation and garbage collection.

Garbage collectors make assumptions about the way applications use objects, and these are reflected in tunable parameters that can be adjusted for improved performance without sacrificing the power of the abstraction.

There are 5 collectors that you should know if you want to improve the GC in your application. The two most important factors affecting garbage collection performance are total available memory and proportion of the heap dedicated to the young generation.

* Serial Collector
* Parallel Collector
* Garbage-First (G1) Garbage Collector
* The Z Garbage Collector
* Shenandoah Garbage Collector

### JUG (Java users Group)

JUG, or Java User Group is a great way to connect, communicate and collaborate with your developer peers. JUGs can be found on almost every continent with regularly occurring meet-ups.

You can see the JUGs here: https://twitter.com/i/lists/221697230/members, or here https://dev.java/community/jugs/

### Conclusion

Java is not just a programming language. Java is a big thing, with a long history and many contributions.

It has an excellent community and plans to continue growing in the future.

### References

* [4 Pillars of Object-Oriented Programming](https://thiago-1.gitbook.io/high-level-programmer/basics/4-pillars-of-object-oriented-programming)
* [Java History](https://www.baeldung.com/java-history)
* [Java SE OpenSource](https://blogs.oracle.com/javamagazine/post/java-se-open-source-license)
* [Java OpenSource](https://opensource.com/resources/java)
* [Oracle Java SE Support Roadmap](https://www.oracle.com/java/technologies/java-se-support-roadmap.html)
* [Moving the JDK to a Two Year LTS Cadence](https://blogs.oracle.com/java/post/moving-the-jdk-to-a-two-year-lts-cadence)
* [The Java Virtual Machine](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-1.html)
* [Java main() method](https://www.javatpoint.com/java-main-method)
* [GraalVM](https://www.graalvm.org/why-graalvm/)
* [Garbage Collector Implementation](https://docs.oracle.com/en/java/javase/18/gctuning/garbage-collector-implementation.html#GUID-71D796B3-CBAB-4D80-B5C3-2620E45F6E5D)
* [Java User Groups](https://dev.java/community/jugs/)
* [JUG - Program](https://jcp.org/en/procedures/overview)
