# 4 Pillars of Object-Oriented Programming

![](../.gitbook/assets/oop-4pillars.png)

Before we talk about the 4 pillars of OOP, let's understand what is Object-Oriented Programming.

### What is Object-Oriented Programming?

Object-Oriented Programming is one paradigm of programming language. This paradigm tries to solve problems based on objects.

An object is a component that can have attributes and actions. These attributes and actions will help the system deal with real-world problems. One example of an object can be a person, one person can have a name, date of birth and contacts. Contacts can be another object, and this object can have multiple attributes too, like email, phone...

There are other types of paradigms like Functional, Procedural, Declarative... All paradigms have different proposals to solve different types of problems, but in this article, we will only talk about OOP.

### What are the 4 pillars?

If you are using a programming language that supports the OOP, so this programming language will have 4 pillars (Abstraction, Encapsulation, Inheritance, Polymorphism).

Examples of programming language that supports OOP: Smalltalk, Java, C#, PHP...

But what are these 4 pillars?

#### Abstraction

Abstraction is responsible for hiding the complex implementation details. It is very useful to help developers to focus on what an object does rather than how it does.

Example: Let's think of Java Collections.

We don’t need to know how an Array List works deeply to use the add method. Just the method name is enough to understand it. But behind it, there are other methods like grow(), which we don't need to understand deeply.

Think of abstraction in object-oriented programming like using a TV remote control. You don't need to understand the intricate electronics inside the TV to change channels or adjust the volume. The remote control provides an abstract interface that hides the inner workings of the TV, allowing you to interact with it at a higher level.

_**So with this pillar, we simplify complex systems by modeling classes based on their essential characteristics and behaviors while hiding unnecessary details.**_

#### Encapsulation

Encapsulation is responsible for keeping state and logic internal. This means that most of the attributes should not be exposed, the actions (functions) should be exposed, and they are responsible for changing the internal state of the object without exposing the state.

Example: Let's keep the system that contains a Person class, but now our system is a bakery system.

Let's suppose we have two other classes, one called Billing and one called Waitress. The waitress has the billing and can do 2 things.

If you are **not using encapsulation**, the waitress can talk to the person and check the person's wallet and make the payment if the person has enough money. "Please do not do that"

Or you can use encapsulation and the person will receive the billing, and he can check internally if he can pay. If the person has enough money, the payment will be made, otherwise, the person will send an exception saying he doesn't have enough money.

_**So with this pillar, we hide the attributes and expose the actions to change the internal state.**_

#### Inheritance

Inheritance is responsible for providing the ability to have parent and child classes to allow the inheritance of behaviors.

Example: Let's keep the system that contains a Person class, but now our system is a Payroll Management System.

In this system, we have 3 types of Persons, the Person that contains two attributes name and salary, and the action calculateSalary.

The Programmer. The programmer will extend the Person, so it will have the same attributes and methods, but it will have another attribute called, for example, bonusInterview, because the programmer receives an extra per interview. In this case, the programmer must override the calculateSalary and include the bonusInterview in the salary.

The Manager is our third class, and this class will also extend the Person, but will have another attribute. The attribute will be percentageInEarnings. The Manager also has to override the calculateSalary, but in this case, the manager has to check the earnings of the month and then multiply by the percentageInEarnings to calculate the bonus of the salary.

_**So with this pillar, we avoid duplicate code using 'is a' pattern, if we verify that a class 'is a' another class, then we should apply the inheritance**._

#### Polymorphism

Polymorphism is responsible for providing the capability for a class to behave as another class.

Example: Let's keep the system above, the Payroll Management System.

Let's think we have a class personalDepartment that have a list of person and have the task to make the payment of all the employees.

With Polymorphism, we can assume that the Manager and the Programmer will behave the same, as they both know how to calculate the salary. So with that, we just need to call the calculateSalary to know the salary of the employees independent of the type of the employee.

If we need another class, like President that has more bonus to the salary, the behavior will be the same in a high view, because the President will also have the method calculateSalary, but with more attributes, because it's a high salary.

_**So with this pillar, we provide the capability to a class behave as another class**_

### Conclusion

There is more to know about OOP, but now you know the basics of the 4 pillars of OOP.

These 4 pillars are the key to writing better software with OOP. It is very important to continue studying these pillars to stay sharp with them.

### References

[The Four Pillars of Object Oriented Programming](https://backend.turing.edu/module1/lessons/four\_pillars\_of\_oop)

[Four Pillars of Object Oriented Programming (OOP)](https://medium.com/@hamzzza.ahmed95/four-pillars-of-object-oriented-programming-oop-e8d7822aa219)

[The Four Pillars of Object-Oriented Programming](https://www.freecodecamp.org/news/four-pillars-of-object-oriented-programming/)

[The Forgotten History of OOP](https://medium.com/javascript-scene/the-forgotten-history-of-oop-88d71b9b2d9f)
