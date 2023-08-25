# General Best Practices

* [Prefer Pure Functions and Avoid Output Parameters](#Prefer-Pure-Functions-and-Avoid-Output-Parameters)
* [Keep the Business Logic in Service Layer](#Keep-the-Business-Logic-in-Service-Layer)
* [Avoid Over-Engineering and Refactor Often](#Avoid-Over-Engineering-and-Refactor-Often)

Here are some general programming guidelines that can be beneficial to write good codes.

## Prefer Pure Functions and Avoid Output Parameters

Pure functions are one of main building blocks of functional programming languages, but not limited to them. 
Even in object-oriented programming, pure functions are easier to understand, test and maintain, 
so it is highly encouraged to make functions and methods pure whenever possible. 
Especially the functions with output parameters make codes much harder to read and easier to introduce bugs, so they should be avoided.

### References
* [Pure function vs impure function](https://www.educative.io/answers/pure-function-vs-impure-function)
* [Code Smell: Output Parameters](https://medium.com/thinkster-io/code-smell-output-parameters-fcb90e0005aa)

## Keep the Business Logic in Service Layer

Microservices usually follow Port and Adapter (a.k.a Hexagonal), Onion (a.k.a Layered) or Clean Architecture (from Uncle Bob). 
The fundamental ideas of those three architectures are [pretty much the same](https://blog.ploeh.dk/2013/12/03/layers-onions-ports-adapters-its-all-the-same/).
Many frameworks provide ways to work on layers easily.
In case Java / Spring, Spring controllers are “adapters” for ports to get user inputs,
and their responsibility is only about receiving the requests and sending the responses back.
Controllers should be thin and light-weighted and business logic should be handled by the service classes.
Putting business logic in the controller is a violation of the single responsibility principle and makes it harder to read, test and maintain the code.

### References
* [Your controllers are doing too much](https://medium.com/swlh/your-controllers-are-doing-too-much-this-is-how-to-simplify-them-7f7d0ea0a810#:~:text=Let%20me%20tell%20you%20this,between%20is%20not%20its%20responsibility.)
* [Decoupling business logic from controllers using service layer](https://boer.dev/decoupling-business-logic-from-controllers-using-a-service-layer)

## Keep the level of abstraction

Proper length of functions or methods are one of controversial topics in programming. 
There are several guidelines that conflict with each other. 
It is usually better to focus on the level of abstraction rather than the length itself. 
All software is built upon several layers of abstraction (from lowest level machine code to the highest level business logic), 
and it is better to keep the level of abstraction in a single function or method for better readability. 
Unfortunately, this is easier said than done. 
One of the easiest ways (although not perfect) is avoid the deep nests. 
In many cases each level of the nest brings the code to the lower abstraction level, 
so it is better to avoid multiple levels of nests and extract those codes into separate helper functions.

* [Code Smell: Changing Levels of Abstraction](https://medium.com/thinkster-io/code-smell-changing-levels-of-abstraction-521cfc8094a2)
* [Why you shouldn’t nest your code](https://www.youtube.com/watch?v=CFRhGnuXG-4)

## Avoid Over-Engineering and Refactor Often

When writing code, performance, scalability and extensibility are important factors. 
However, if overdone, those can make code overly complicated and reduce productivity. 
There are reasons that these principles are often mentioned:

* Premature optimization is the root of all evil
* KISS (Keep it short and simple, or Keep it simple, stupid)
* YAGNI (You Aren’t Gonna Need It)

Agile software development is based on continuous delivery of working software for ever-changing requirements by iterating short development cycles. 
In order to meet those principles, over-engineering should be avoided and simpler solutions are usually implemented.
However, as more requirements are added, software becomes inherently complicated. 
Although [accidental / incidental complexity needs to be avoided, essential complexity cannot be](https://dev.to/alexbunardzic/software-complexity-essential-accidental-and-incidental-3i4d). 
As essential complexity grows, previous simpler solutions can become tech debts due to the lack of upfront design, and add accidental complexity.
In order to manage the complexity and code quality, frequent refactor is essential, especially in agile environments before [broken window theory](https://medium.com/@learnstuff.io/broken-window-theory-in-software-development-bef627a1ce99) applies.

### References
* [The 12 principles behind the Agile Manifesto](https://www.agilealliance.org/agile101/12-principles-behind-the-agile-manifesto/)
* [Overengineering: What is it and how to make sure you don’t overpay](https://madappgang.com/blog/overengineering/)
* [Why is refactoring your code important in Agile?](https://www.coscreen.co/blog/refactoring-your-code-in-agile/)
* [Code Quality: Debunking the Speed vs Quality Myth with Empirical Data](https://codescene.com/blog/code-quality-debunking-the-speed-vs-vs-quality-myth-with-empirical-data)



