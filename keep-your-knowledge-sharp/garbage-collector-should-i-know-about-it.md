# Garbage Collector, should I know about it?

If you work with Java, you probably have already heard about GC(Garbage collector), but do you know how it works, or how can you tune the JVM?

### Garbage Collector

The garbage collector (GC) automatically manages the application's dynamic memory allocation requests.

A garbage collector performs automatic dynamic memory management through the following operations:

* Allocates from and gives back memory to the operating system.
* Hands out that memory to the application as it requests it.
* Determines which parts of that memory is still in use by the application.
* Reclaims the unused memory for reuse by the application.

There are some Garbage collectors, but we will talk about just 3 of them, the most common:

#### **Parellel GC**

The parallel collector is also known as the throughput collector, it's a generational collector similar to the serial collector. The primary difference between the serial and parallel collectors is that the parallel collector has multiple threads that are used to speed up garbage collection.

The parallel collector is intended for applications with medium-sized to large-sized data sets that are run on multiprocessor or multithreaded hardware. You can enable it by using the -XX:+UseParallelGC option.

#### **G1GC**

The Garbage-First (G1) garbage collector is targeted for multiprocessor machines with a large amount of memory. It attempts to meet garbage collection pause-time goals with high probability while achieving high throughput with little need for configuration.

The Garbage-First garbage collector is the default collector since Java 11, so typically you don't have to perform any additional actions. You can explicitly enable it by providing -XX: +UseG1GC on the command line.

G1 becomes the default because limiting GC pause times is, in general, more important than maximizing throughput. Switching to a low-pause collector such as G1 should provide a better overall experience, for most users, than a throughput-oriented collector such as the Parallel GC, which was currently the default.

#### **ZGC**

The Z Garbage Collector (ZGC) is a scalable low latency garbage collector. ZGC performs all expensive work concurrently, without stopping the execution of application threads.

ZGC is intended for applications which require low latency (less than 10 ms pauses) and/or use a very large heap (multi-terabytes). You can enable is by using the -XX: +UseZGC option.

### **Which Garbage Collector should I choose?**

If you still don't know what to choose, you can follow these guidelines as a starting point:

• If the application has a small data set (up to approximately 100 MB), then select the serial collector with the option -XX:+UseSerialGC. \
• If the application will be run on a single processor and there are no pause-time requirements, then select the serial collector with the option -XX:+UseSerialGC. \
• If (a) peak application performance is the first priority and (b) there are no pausetime requirements or pauses of one second or longer are acceptable, then let the VM select the collector or select the parallel collector with -XX:+UseParallelGC. \
• If response time is more important than overall throughput and garbage collection pauses must be kept shorter than approximately one second, then select a mostly concurrent collector with -XX:+UseG1GC or -XX:+UseConcMarkSweepGC. \
• If response time is a high priority, and/or you are using a very large heap, then select a fully concurrent collector with -XX:UseZGC.

### Ergonomics

Ergonomics is the process by which the Java Virtual Machine (JVM) and garbage collection heuristics, such as behavior-based heuristics, improve application performance.

Do you know the default values the JVM choose for your application?

If you don't know, please, don't use the default values. But, just to be aware of the default ergonomics:

The defaults will change according to your server configuration. For example, if the JVM is configured not a server-class machine, the default will be Serial GC with this configuration:

• the client JVM \
• the serial garbage collector \
• Initial heap size of 4MB \
• Maximum heap size of 64MB

However, I suppose we are talking about server-class machine, and with Java 11 or above, with this configuration the default will be:

• G1 garbage collector \
• Initial heap size of 1/64 of physical memory \
• Maximum heap size of 1/4 of physical memory\


Note: Server-class machine are defined as machine with 2 or more physical CPU's and 2 or more GB RAM

### Performance Metrics

Several metrics are utilized to evaluate garbage collector performance, including:

* Throughput—the percentage of total time not spent in garbage collection, considered over long periods of time.
* Garbage collection overhead—the inverse of throughput, that is, the percentage of total time spent in garbage collection.
* Pause time—the length of time during which application execution is stopped while garbage collection is occurring.
* Frequency of collection—how often collection occurs, relative to application execution.
* Footprint—a measure of size, such as heap size.
* Promptness—the time between when an object becomes garbage and when the memory becomes available

### Conclusion

There are many configurations for tuning the GC, and many GC with different proposes.

You should not include many configs to tune your JVM without know what are you doing, and you should also not depend just on JVM ergonomics. Besides on that, you should at least configure the GC your application you use and also the -Xmx (maximum heap size). The others tuning variables you should use according to your application and your needs.



### References

* [Server class definition code](https://github.com/openjdk/jdk/blob/3121898c33fa3cc5a049977f8677105a84c3e50c/src/hotspot/share/runtime/os.cpp#L1673)
* [JDK 11 - ergonomics code](https://hg.openjdk.java.net/jdk/jdk11/file/1ddf9a99e4ad/src/hotspot/share/runtime/arguments.cpp#l3898)
* [HotSpot Virtual Machine Garbage Collection Tuning Guide - Java SE 19](https://docs.oracle.com/en/java/javase/19/gctuning/hotspot-virtual-machine-garbage-collection-tuning-guide.pdf)
