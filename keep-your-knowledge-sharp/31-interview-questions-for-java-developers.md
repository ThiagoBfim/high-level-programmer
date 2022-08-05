# 31 Interview Questions for Java Developers

Here I'm going to show 31 questions that it's important to know to be prepared for an Interview.

The questions are divided into 3 sections, basics, advanced, and web.

If you are a Junior, maybe just the basics and the web will be enough.

Hope this help, and if you want to help, send me a PR :smile:

**PS:** I'm not going to show you deep answers, if you don't master some of these questions, I recommend you study them more.

### Java Basics

**1. How should we compare two objects?**

**Answer:** With the Equals.\
Using Objects.equals to avoid NPE

**2. What are the 4 pillars of Object Orientation?**

**Answer:** abstraction, encapsulation, polymorphism, and inheritance\
You have to know deep each one to explain it.

**3. What are access modifiers in Java?**

**Answer:** default, public, private, protected\
You have to know deep the differences between them.

**4. Let's say I have a list of objects and I want to execute the contains method, what method does my object need to override for me to use the contains in the best way possible?**

**Answer:** Equals e HashCode

**5. Is String immutable? If so, what is it to be immutable?**

**Answer:** Yes, the object is not changed, a new object is created, String uses the Immutability Patterns design.

**6. What is the best class to deal with money in Java?**

**Answer:** BigDecimal, the Decimal has a problem with rounding.

**7. What is the difference between List and Set?**

**Answer:** Set does not accept duplicate elements and has no indexers, so the order is not important, and it also does not allow searching by index.

**8. Which is more performant to add an element, ArrayList ou HashSet?**

**Answer:** HashSet O(1), ArrayList O(n)

**9. Which method is used to count elements in a stream?**

**Answer:** Count\
This is just a simple question about stream, you should know more about it to be able to respond to different types of questions about Stream.

**10. Which method is used to filter a stream?**

**Answer:** Filter

**11. What is a functional interface? What is the difference between Consumer and Predicate?**

**Answer:** Interface functional in Java is an Interface with just one default method. The Consumer receives an element and returns void, forEach for example. The Predicate takes an element and returns a boolean.\
This question talks about the difference between two functional interfaces, but you should also the others.

**12. Can you tell me what Optional is, and what is it for?**

**Answer:** Prevent NullPointerException

**13. Final is a reserved word in Java, how can we use it?**

**Answer:** With a variable to make it impossible to include a new instance.\
With class to block extensions.\
With a method to block override.

### Java Advanced

**14. Can you give me 2 examples of design patterns, and how you use them?**

**Answer:** Strategy, Template Method, Builder, Singleton, Flyweight, Immutability, Observer, Factory…

**15. Is Java Multithread, what does that mean?**

**Answer:** Yes, In Java, Multithreading refers to a process of executing two or more threads simultaneously for maximum utilization of the CPU.

**16. What are the problems we might have with concurrency?**&#x20;

**Answer:** DeadLock, Starvation\
**Starvation:** Resource starvation can occur due to the lack of computer resources or the existence of multiple processes that are competing for the same computer resources.\
**DeadLock:** is a situation in which two computer programs sharing the same resource are effectively preventing each other from accessing the resource, resulting in both programs ceasing to function.

**17. What is the Synchronized reserved word, and what is it used for?**

**Answer:** Ensures that only one thread accesses the resource concurrently.

**18. Can you explain to me what the finally clause is for in a try-catch?**

**Answer:** The finally clause is always executed after the try-catch, even if there is an exception.

**19. Can you tell me what is try-with-resources?**

**Answer:** It is an implementation of try-catch for elements that implement the Closeable interface, and with try-with-resouces we guarantee that the element will be closed after use.

**20. What is SOLID, and how do you use them?**

**Answer:** 5 design principles\
S - Single-responsiblity principle\
O - Open-closed principle\
L - Liskov substitution principle\
I - Interface segregation principle\
D - Dependency Inversion Principle\
You should know how to use them.

**21. Do you know what is clean code, can you give me an example?**

**Answer:** Clean code is a practice to keep the code easier to understand. Some examples: 3 or fewer parameters, methods with few lines, small classes, clear names...

**22. Give me two types of Garbage Collectors, and what is it?**

**Answer:** Serial Collector, Parallel Collector, G1 (Garbage First). In Java, the process of deallocating memory is handled automatically by the garbage collector.\
It's also useful to know the 3 sections of the GC, the Young generation, the Old generation, and the Permanent generation.

**23. What type of memories exists in the JVM?**

**Answer:** Heap and non-heap.\
The Heap area is the memory block where objects are created or objects are stored.\
Non-heap is divided into 4 categories:\
**Class(Method) Area:** used to store information about the classes that have been loaded. Constrained by MaxMetaspaceSize.\
**Stack/Thread:** memory used by threads in the JVM. A function of the number of threads that are running. The Stack memory also stores primitive types.\
**Program Counter Register:** A program counter register is linked with each JVM thread that carries out the task of a specific method.\
**Native Method Stack:** Native method stacks are also called C stacks. They are not written in the Java language. For each thread, this memory is allocated when it is created.

**24. Where primitives are stored in Java?**

**Answer:** stack memory. Only local primitive variables and references to object (i.e. variable declared in method) are stored in stack. Others are stored in heap.

### Java Web

**25. About REST, what are the main methods and their differences?**

**Answer:** POST, DELETE, GET, PUT, PATCH\
You should know the difference and when to use them.

**26. What is a JWT(Json web token)?**

**Answer:** JWT is a token to contain and transmit information about a particular user or session. JWT is separated into 3 parts, Header (signature algorithm), Payload (claims, user data) and Signature (security guarantee)

**27. What is Idempotent?**

**Answer:** A request method is considered "idempotent" if the intended effect on the server of multiple identical requests with that method is the same as the effect for a single request of that type. Of the request methods defined by this specification, PUT, DELETE, and secure request methods are idempotent. According to RFC9110.

**28. Do you know Richardson's Maturity Model, or what is Hypermedia Controls?**

**Answer:** A model (developed by Leonard Richardson) that breaks down the principal elements of a REST approach into three steps. These introduce resources, HTTP verbs, and hypermedia controls.\
Hypermedia is the last level.

**29. Do you know what is XSS, and how to prevent it?**

**Answer:** Cross Site Scripting can occur on the malicious script executed at the client side. Avoid  allowing any type of JavaScript in the content of the application, and include a good CORs configuration.\
If you don't know about CORs(Cross-origin resource sharing), I recommend you to study it.

**30. What is CDI (Contexts and Dependency Injection)?**

**Answer:** The ability to inject components into an application in a typesafe way, including the ability to choose at deployment time which implementation of a particular interface to inject.

**31. What is Spring Bean?**

**Answer:** By definition, a Spring bean is an object that forms the backbone of your application and that is managed by the Spring IoC( Inversion of Control) container.\
A bean is an object that is instantiated, assembled, and otherwise managed by a Spring IoC container.\
This question can be made differently, asking about IoC, so be aware of it.

### Conclusion

Each interviewer can ask different things, and in different ways, so be prepared to live code, code challenges, code review, and other types. Another important thing is to know about agile practices, cloud, Kubernetes, microservices, and other's things that could be asked.

There are many questions that you may see during an interview. But if you know these 31 questions, you will be much more prepared for an interview.

Hope this helps you :)

### References

* [Awesome Java Inteview Questions](https://github.com/DopplerHQ/awesome-interview-questions#java)
* [Java Inteview Questions](https://github.com/learning-zone/java-interview-questions)
* [RFC9110](https://www.rfc-editor.org/rfc/rfc9110#name-idempotent-methods)\
