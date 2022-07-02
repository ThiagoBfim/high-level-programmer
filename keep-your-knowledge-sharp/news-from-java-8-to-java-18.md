# News from Java 8 to Java 18

Here I will include some news in each version of Java, perhaps the most important, at least for development, but remember, there will be more things to know about this, there are several new things done internally that help a lot.

Before starting, it is important to know the difference between LTS and non-LTS version, and how the releases work now.

The LTS version is the Long-Term-Support, so they have more support than the others.

Since Java 17, the release program has been 2 new releases every year, one in March and one in September, and the interval between LTS versions is now two years instead of three, making Java 21 (planned for September 2023) probably the next LTS.

If you want to know more about it: https://www.oracle.com/java/technologies/java-se-support-roadmap.html

### Java 8 (LTS)

This is our first LTS release that we will talk about here. There are many projects that still use this version, as this version has extended support until December 2030.

But beware, there are many tools and frameworks that stop supporting this version, and the new versions contain new features that will help you gain productivity.

I'll show just some news in this version because this is a big version with a lot of news. Like LocalDate, LocalDateTime, updates into File API...

If you want to know more about what's new in Java 8: https://www.baeldung.com/java-8-new-features https://www.oracle.com/java/technologies/javase/8-whats-new.html

#### Stream

Java supports a sequence of operations that can be executed in parallel or sequential and with Lazy execution.

Example:

```
int sum = widgets.stream()
                     .filter(w -> w.getColor() == RED)
                     .mapToInt(w -> w.getWeight())
                     .sum();
```

The Stream in Java contains two types of operations: terminal and intermediate. We can have multiple intermediate operations, but only one terminal operation for producing the result or the side effect.

Streams are lazy; computation on the source data is only performed when the terminal operation is initiated, and source elements are consumed only as needed.

If you want to know more about it: [https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html)

#### The most common Functional Interfaces

Functional interfaces provide target types for lambda expressions and method references. Each functional interface has a single abstract method, called the functional method for that functional interface, to which the lambda expression's parameter and return types are matched or adapted. Functional interfaces can provide a target type in multiple contexts, such as assignment context, method invocation, or cast context:

Most common Functional Interface:

* Consumer: Represents an operation that accepts a single input argument and returns no result.
* Function\<T,R>: Represents a function that accepts one argument and produces a result.
* Predicate: Represents a predicate (boolean-valued function) of one argument.
* Supplier: Represents a supplier of results.

If you want to know more about it: https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html

#### Optional

A container object which may or may not contain a non-null value. If a value is present, isPresent() will return true and get() will return the value.

Optional should be used to avoid NPE(NullPointerException)

If you want to know more about it: [https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html)

### Java 9

If you want to know more about what's new in Java 9: [https://www.oracle.com/java/technologies/javase/9-all-relnotes.html](https://www.oracle.com/java/technologies/javase/9-all-relnotes.html)

[https://www.baeldung.com/new-java-9](https://www.baeldung.com/new-java-9)

#### Modules

Java changes a lot from version 8 to version 9 because of Modules.

![Image](https://intexsoft.com/app/uploads/2021/08/java8-x-java9.jpg)

According to JSR 376, the key goals of modularizing the Java SE platform are:

* Reliable configuration
* Strong encapsulation
* Scalable Java platform
* Greater platform integrity
* Improved performance

_"Each module must explicitly state its dependencies. "_

_"A key motivation of the module system is strong encapsulation."_

If you want to know more about java Modules: __ [https://www.oracle.com/pt/corporate/features/understanding-java-9-modules.html](https://www.oracle.com/pt/corporate/features/understanding-java-9-modules.html)

#### Improvements Java 9

**takeWhile**

_default Stream takeWhile(Predicate\<? super T> predicate)_

Returns, if this stream is ordered, a stream consisting of the longest prefix of elements taken from this stream that match the given predicate. Otherwise returns, if this stream is unordered, a stream consisting of a subset of elements taken from this stream that match the given predicate.

_The takeWhile operation will keep elements while the given predicate for an element returns true;_

**dropWhile**

_default Stream dropWhile(Predicate\<? super T> predicate)_

Returns, if this stream is ordered, a stream consisting of the remaining elements of this stream after dropping the longest prefix of elements that match the given predicate. Otherwise returns, if this stream is unordered, a stream consisting of the remaining elements of this stream after dropping a subset of elements that match the given predicate.

_The dropWhile operation will remove elements while the given predicate for an element returns true and stops removing on the first predicate's false._

**iterate**

_public static Stream iterate(T seed, Predicate\<? super T> hasNext, UnaryOperator next)_

Returns a sequential ordered Stream produced by iterative application of the given next function to an initial element, conditioned on satisfying the given hasNext predicate. The stream terminates as soon as the hasNext predicate returns false.

_This operation is Lazy too._

For more information: [https://www.baeldung.com/java-9-stream-api](https://www.baeldung.com/java-9-stream-api)

### Java 10

If you want to know more about what's new in Java 10: [https://www.oracle.com/java/technologies/javase/10-relnote-issues.html ](https://www.oracle.com/java/technologies/javase/10-relnote-issues.html)[https://www.baeldung.com/java-10-overview](https://www.baeldung.com/java-10-overview)

#### Unmodifiable List in the Collection

Several new APIs have been added that facilitate the creation of unmodifiable collections. The List.copyOf, Set.copyOf, and Map.copyOf methods create new collection instances from existing instances.

Example:

```
List<Integer> newList = Lists.copyOf(otherList);
```

#### Optional.orElseThrow()

A new method orElseThrow has been added to the Optional class. It is synonymous with and is now the preferred alternative to the existing get method.

**API Note: The preferred alternative to the method get() is orElseThrow().**

#### Var: Local-Variable Type Inference

For local variable declarations with initializers, enhanced for-loop indexes, and index variables declared in traditional for loops, allow the reserved type name var to be accepted in place of manifest types:

```
var list = new ArrayList<String>(); // infers ArrayList<String>
var stream = list.stream();         // infers Stream<String>
```

If you want to know more about it: [https://openjdk.org/jeps/286](https://openjdk.org/jeps/286)

### Java 11 (LTS)

This is an LTS version, has a extended support until September 2026

If you want to know more about what's new in Java 11: [https://www.oracle.com/java/technologies/javase/11-relnote-issues.html](https://www.oracle.com/java/technologies/javase/11-relnote-issues.html)

[https://www.baeldung.com/java-11-new-features](https://www.baeldung.com/java-11-new-features)

#### New methods to String

Java 11 adds a few new methods to the String class: isBlank, lines, strip, stripLeading, stripTrailing, and repeat.

#### New methods to File

We can use the new readString and writeString static methods from the Files class

```
public static String readString(Path path);

public static Path writeString(Path path, CharSequence csq, OpenOption... options);
```

#### Predicate.not

Returns a predicate that is the negation of the supplied predicate. This is accomplished by returning the result of the calling target.negate().

```

var newListWithoutBlank = myList.stream()
  .filter(Predicate.not(String::isBlank))
  .collect(Collectors.toList());
```

#### HTTP Client (Standard)

The HTTP Client has been standardized in Java 11. As part of this work the previously incubating API, located in the jdk.incubator.http package, has been removed. At a very minimum, code that uses types from the jdk.incubator.http package will need to be updated to import the HTTP types from the standard package name, java.net.http.

The new HTTP API improves overall performance and provides support for both HTTP/1.1 and HTTP/2:

```
HttpClient httpClient = HttpClient.newBuilder()
  .version(HttpClient.Version.HTTP_2)
  .connectTimeout(Duration.ofSeconds(20))
  .build();
HttpRequest httpRequest = HttpRequest.newBuilder()
  .GET()
  .uri(URI.create("https://google.com"))
  .build();
HttpResponse httpResponse = httpClient.send(httpRequest, HttpResponse.BodyHandlers.ofString());
```

### Java 12

If you want to know more about what's new in Java 12: [https://www.oracle.com/java/technologies/javase/12-relnote-issues.html](https://www.oracle.com/java/technologies/javase/12-relnote-issues.html)

[https://www.baeldung.com/java-12-new-features](https://www.baeldung.com/java-12-new-features)

This version introduces new things that are just a preview. It is possible to change the config to use the preview features, but in this version, some of them were not prepared for production.

#### Compact Number Formatting

Java 12 comes with a new number formatter – the CompactNumberFormat. It's designed to represent a number in a shorter form, based on the patterns provided by a given locale.

```
NumberFormat likesShort =
NumberFormat.getCompactNumberInstance(new Locale("en", "US"), NumberFormat.Style.SHORT);
likesShort.setMaximumFractionDigits(2);
assertEquals("2.59K", likesShort.format(2592));

NumberFormat likesLong =
NumberFormat.getCompactNumberInstance(new Locale("en", "US"), NumberFormat.Style.LONG);
likesLong.setMaximumFractionDigits(2);
assertEquals("2.59 thousand", likesLong.format(2592));
```

### Java 13

If you want to know more about what's new in Java 13: [https://www.oracle.com/java/technologies/javase/13-relnote-issues.html](https://www.oracle.com/java/technologies/javase/13-relnote-issues.html)

[https://www.baeldung.com/java-13-new-features](https://www.baeldung.com/java-13-new-features)

#### Added FileSystems.newFileSystem(Path, Map\<String, ?>) Method

Three new methods have been added to java.nio.file.FileSystems to make it easier to use file system providers that treat the contents of a file as a file system.

```
newFileSystem(Path)
newFileSystem(Path, Map<String, ?>)
newFileSystem(Path, Map<String, ?>, ClassLoader)
```

### Java 14

If you want to know more about what's new in Java 14: [https://www.oracle.com/java/technologies/javase/14-relnote-issues.html ](https://www.oracle.com/java/technologies/javase/14-relnote-issues.html)[https://www.baeldung.com/java-14-new-features](https://www.baeldung.com/java-14-new-features)

#### Switch Expressions (JEP 361)

Extend switch so it can be used as either a statement or an expression.

```
int numLetters = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> 6;
    case TUESDAY                -> 7;
    case THURSDAY, SATURDAY     -> 8;
    case WEDNESDAY              -> 9;
};
```

#### Text Blocks (JEP 368 Second Preview)

Add text blocks to the Java language. A text block is a multi-line string literal that avoids the need for most escape sequences, automatically formats the string in a predictable way, and gives the developer control over the format when desired.

```
String html = """
              <html>
                  <body>
                      <p>Hello, world</p>
                  </body>
              </html>
              """;
```

#### Records (JEP 359 Preview)

Records provide a compact syntax for declaring classes that are transparent holders for shallowly immutable data.

```
public record User(int id, String password) { };
```

#### Pattern Matching for instanceof (JEP 305 Preview)

JDK 14 has introduced pattern matching for instanceof with the aim of eliminating boilerplate code and making the developer's life a little bit easy.

```
if (obj instanceof String str) {
    int len = str.length();
    // ...
}
```

#### Helpful NullPointerExceptions (JEP 358)

Improve the usability of NullPointerExceptions generated by the JVM by describing precisely which variable was null.

```
a.b.c.i = 99;

Exception in thread "main" java.lang.NullPointerException:
        Cannot read field "c" because "a.b" is null
    at Prog.main(Prog.java:5)
```

### Java 15

In this version, the Text Blocks is a fully supported product feature in Java 15 (JEP 378).

If you want to know more about what's new in Java 15: [https://www.oracle.com/java/technologies/javase/15-relnote-issues.html](https://www.oracle.com/java/technologies/javase/15-relnote-issues.html)

[https://www.baeldung.com/java-15-new](https://www.baeldung.com/java-15-new)

#### Sealed Classes (JEP 360 Preview)

Before Sealed Classes, Java doesn't provide any fine-grained control over the inheritance. Sealed classes solve this problem. Sealed classes and interfaces restrict which other classes or interfaces may extend or implement them.

It's important to note that any class that extends a sealed class must itself be declared sealed, non-sealed, or final. This ensures the class hierarchy remains finite and known by the compiler.

```
public abstract sealed class Shape
    permits Circle, Rectangle, Square {...}

public final class Circle extends Shape {...}

public sealed class Rectangle extends Shape
    permits TransparentRectangle, FilledRectangle {...}
public final class TransparentRectangle extends Rectangle {...}
public final class FilledRectangle extends Rectangle {...}

public non-sealed class Square extends Shape {...}
```

Sealed classes work well with records (JEP 384), another preview feature of Java 15. Records are implicitly final, so a sealed hierarchy with records is slightly more concise than the example above:

```
public sealed interface Expr
    permits ConstantExpr, PlusExpr, TimesExpr, NegExpr {...}

public record ConstantExpr(int i)       implements Expr {...}
public record PlusExpr(Expr a, Expr b)  implements Expr {...}
public record TimesExpr(Expr a, Expr b) implements Expr {...}
public record NegExpr(Expr e)           implements Expr {...}
```

### Java 16

The Records is a fully supported product feature in Java 16 (JEP 395).

The Pattern Matching for instanceof is a fully supported product feature in Java 16 (JEP 394).

In this version, the codebase was migrated to GitHub ([https://github.com/openjdk/](https://github.com/openjdk/)) by JEB 369

If you want to know more about what's new in Java 16: [https://www.oracle.com/java/technologies/javase/16-relnote-issues.html](https://www.oracle.com/java/technologies/javase/16-relnote-issues.html)

[https://www.baeldung.com/java-16-new-features](https://www.baeldung.com/java-16-new-features)

#### Stream.toList Method (JDK-8180352)

The aim is to reduce the boilerplate with some commonly used Stream collectors, such as Collectors.toList and Collectors.toSet:

```
List<Integer> ints = integersAsString.stream().map(Integer::parseInt).collect(Collectors.toList());
List<Integer> intsEquivalent = integersAsString.stream().map(Integer::parseInt).toList();
```

#### Warnings for Value-Based Classes

Users of the value-based classes provided by the standard libraries—notably including users of the primitive wrapper classes—should avoid relying on the identity of class instances. Programmers are strongly discouraged from calling the wrapper class constructors, which are now deprecated for removal. New javac warnings discourage synchronization on value-based class instances. Runtime warnings about synchronization can also be activated, using command-line option -XX:DiagnoseSyncOnValueBasedClasses.

For further details, see JEP 390.

The [Valhalla Project](https://openjdk.org/projects/valhalla/) is pursuing a significant enhancement to the Java programming model in the form of primitive classes. Such classes declare their instances to be identity-free and capable of inline or flattened representations, where instances can be copied freely between memory locations and encoded using solely the values of the instances' fields.

### Java 17 (LTS)

This is a LTS version, have a extended support until September 2029

The Sealed Classes is fully supported product feature in Java 17 (JEP 409).

If you want to know more about what's new in Java 17: [https://www.oracle.com/java/technologies/javase/17-relnote-issues.html](https://www.oracle.com/java/technologies/javase/17-relnote-issues.html)

[https://www.baeldung.com/java-17-new-features](https://www.baeldung.com/java-17-new-features)

#### Deprecate the Applet API for Removal (JEP 398)

Deprecate the Applet API for removal. It is essentially irrelevant since all web-browser vendors have either removed support for Java browser plug-ins or announced plans to do so.

The Applet API was previously deprecated, though not for removal, by JEP 289 in Java 9.

#### Pattern Matching for Switch (JEP 406 Preview)

Extending pattern matching to switch allows an expression to be tested against a number of patterns, each with a specific action, so that complex data-oriented queries can be expressed concisely and safely.

```
Object o = 123L;
String formatted = switch (o) {
    case Integer i -> String.format("int %d", i);
    case Long l    -> String.format("long %d", l);
    case Double d  -> String.format("double %f", d);
    case String s  -> String.format("String %s", s);
    default        -> o.toString();
};
```

#### Strongly Encapsulate JDK Internals (JEP 403)

Strongly encapsulate all internal elements of the JDK, except for critical internal APIs such as sun.misc.Unsafe. It will no longer be possible to relax the strong encapsulation of internal elements via a single command-line option, as was possible in JDK 9 through JDK 16.

Over the years the developers of various libraries, frameworks, tools, and applications have used internal elements of the JDK in ways that compromise security and maintainability.

### Java 18

If you want to know more about what's new in Java 18: [https://www.oracle.com/java/technologies/javase/18-relnote-issues.html](https://www.oracle.com/java/technologies/javase/18-relnote-issues.html)

#### UTF-8 by Default (JEP 400)

Starting with JDK 18, UTF-8 is the default charset for the Java SE APIs. APIs that depend on the default charset behave consistently across all JDK implementations and independently of the user’s operating system, locale, and configuration. Specifically, java.nio.charset.Charset#defaultCharset() now returns UTF-8 charset by default. The file.encoding system property is now a part of the implementation specification, which may accept UTF-8 or COMPAT. The latter is a new property value that instructs the runtime to behave as previous releases. This change is significant to users who call APIs that depend on the default charset. Users can determine whether they'd be affected or not, by specifying -Dfile.encoding=UTF-8 as the command line option with the existing Java runtime environment.

#### Deprecate Finalization for Removal (JEP 421)

The finalization mechanism has been deprecated for removal in a future release. The finalize methods in standard Java APIs, such as Object.finalize() and Enum.finalize(), have also been deprecated for removal in a future release, along with methods related to finalization, such as Runtime.runFinalization() and System.runFinalization().

Finalization remains enabled by default, but it can be disabled for testing purposes by using the command-line option --finalization=disabled introduced in this release. Maintainers of libraries and applications that rely upon finalization should migrate to other resource management techniques in their code, such as [try-with-resources](https://dev.java/learn/catching-and-handling-exceptions/#anchor\_6) and [cleaners](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/ref/Cleaner.html).

#### Code Snippets in Java API Documentation (JEP 413)

An @snippet tag for JavaDoc's Standard Doclet has been added, to simplify the inclusion of example source code in API documentation.

For further details, see [Programmer's Guide to Snippets](https://docs.oracle.com/en/java/javase/18/code-snippet/index.html).

### Conclusion

Java changed a lot, now there are many things that help the day-to-day developers.

This article is just an introduction to what's new in Java. There are many other things, and improvements to the JVM and the Garbage Collector.

So keep studying and keep in touch with the news from Java :smile:

### References

[JEPS Search](https://chriswhocodes.com/jepsearch.html)

[Java SE Release notes](https://www.oracle.com/java/technologies/javase/jdk-relnotes-index.html)
