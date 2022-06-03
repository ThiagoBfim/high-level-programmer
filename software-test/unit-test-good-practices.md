# Unit Test - Good Practices

We will talk about unit tests, they are generally more common to be done, and should be done in greater quantity.

![Test Pyramid](https://miro.medium.com/max/828/1\*NFxH-0MSEC5NQU-eCxX7Tw.png)

### Benefits of unit tests

Unit tests bring many benefits to the software, I'll show you some of them:

* More safety to do maintenance and new features.
* Provide a way to have more concise code.
* It can serve as documentation for other developers

**“Legacy Code is code without Tests.”**\
_―_ Michael Feathers

### Good practices for creating a unit test

To understand how the tests should behave, let's first understand two acronyms, the **FIRST** and the **CORRECT.**

Those who know TDD (Test Driven Development), follow the pattern of writing the test first, after failing, writing the code to pass the test, and keep doing this until the development is finished.

The FIRST acronyms will help us to write tests following some essential rules, and can be used with TDD or without it:

**Fast:** The Faster, the Better. The ideal is not to depend on external integrations, like file directory, internet, database...

**Independent:** The test can't depend on other tests. The unit test has to be able to run independently without caring about the order.

**Repeatable:** The unit test can be run multiple times and the result should always be the same.

**Self Validating:** Each test needs at least one assertion to validate the execution

**Timely:** The unit test needs to have smart coverage, trying to find all the boundaries, to ensure the test will validate all the scenarios.\
They also need to be done at the right time. By creating the test first, you ensure your code more quality.

In addition to tests being FIRST, it is also necessary to think that it must be CORRECT.

**CORRECT** is useful to validate if your test is good. For that, you have to answer these questions:

**Conformity:** Does the data represent the correct type?

**Order**: Is the order of the result as expected?

**Range**: Are you validating the range of the data?

**Reference**: Does the test call any external service?

**Existence**: Can the unit test value be null or negative?

**Cardinality**: There is enough value?

**Time**: Is everything running in some order? Is it safe with concurrency?&#x20;

### Test Nomenclature





&#x20;

****



