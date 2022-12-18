---
cover: https://miro.medium.com/max/1400/1*qTX5NbS5PFZxUQydg-BoAg.png
coverY: -50.10224948875255
---

# SOLID - Direct Way

### SOLID

SOLID is an acronym coined in the 2004s by Michael Feathers based on some principles presented by Robert C. Martin around the 2000s.

The SOLID principles tell us how to arrange our functions and data structures into classes, and how those classes should be interconnected. The use of the word “class” does not imply that these principles are applicable only to object-oriented software. A class is simply a coupled grouping of functions and data. Every software system has such groupings, whether they are called classes or not. The SOLID principles apply to those groupings.

### Design Principles

Software Design Principles are a set of guidelines that helps developers to make a good system design

We can make a metaphor in relation to design patterns:

_A building with good architecture but poorly made bricks will not result in good construction._\
_On the other hand, even with good bricks and architecture, if the interconnection between the bricks is not of good quality, the construction will also not be satisfactory._

That's why principles are of great value

### \[SRP] - The Single Responsibility Principle

> "Gather together the things that change for the same reasons. Separate things that change for different reasons."\
> **-** Robert C. Martin

An active corollary to Conway’s law: The best structure for a software system is heavily influenced by the social structure of the organization that uses it so that each software module has one, and only one, reason to change.

### \[OCP] - The Open-Closed Principle

> "A Module should be open for extension but closed for modification."\
> **-** Robert C. Martin

Bertrand Meyer made this principle famous in the 1980s. The gist is that for software systems to be easy to change, they must be designed to allow the behavior of those systems to be changed by adding new code, rather than changing existing code.

### \[LSP] - The Liskov Substitution Principle

> "A program that uses an interface must not be confused by an implementation of that interface."\
> **-** Robert C. Martin

Barbara Liskov’s famous definition of subtypes, from 1988. In short, this principle says that to build software systems from interchangeable parts, those parts must adhere to a contract that allows those parts to be substituted one for another.

### \[ISP] - Interface Segregation Principle

> "Keep interfaces small so that users don’t end up depending on things they don’t need."\
> **-** Robert C. Martin

This principle advises software designers to avoid depending on things that they don’t use.

### \[DIP] -The Dependency Inversion Principle

> "Depend on the direction of abstraction. High-level modules should not depend upon low-level details."\
> **-** Robert C. Martin

The code that implements high-level policy should not depend on the code that implements low-level details. Rather, details should depend on policies.

### Conclusion

The design principle will help you write better code. Hope you now know more about it and can enjoy its benefits.

These design principles, when properly applied, can offer:

* Code quality
* Easier to maintain
* Tolerant of change
* Easier to test
* More understandable

### References

**Clean Architecture**\
\*\*\*\*- Robert Cecil Martin

[Software Design Principles Every Programmer Should Know](https://medium.com/@peterlee2068/software-design-principles-every-programmer-should-know-c164a83c6f87)

[Unity Best Practices](https://jaayap.github.io/Unity\_Best\_Practices/En/CleanCode.html)

[Applying SOLID with OCR project](https://github.com/ThiagoBfim/SOLID-OCR)
