![Software Architecture](https://i.redd.it/tn56h6svoql21.jpg)

## Layered Architecture

[The layered architecture pattern](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html),
a.k.a. n-tier architecture pattern is historically most well known and popular architectural pattern.

![Layered Architecture](https://www.oreilly.com/api/v2/epubs/9781491971437/files/assets/sapr_0101.png)

In this architucture, components are organized into horizontal layers, with the presentation at the top and the database at the bottom.
Layered architecture is a popular architecture used for traditional applications for a long time,
but [it has limitations](https://www.linkedin.com/pulse/revisiting-layered-architecture-recognizing-building-riad-ahmed/).
Especially, having the database as a foundation layer, layered architecture tends to be focused on database structured rather than the use cases.

## Hexagonal / Onion / Clean<sup>TM</sup> Architectures

Hexagonal / Onion / Clean<sup>TM</sup> architectures are popular alternatives to the layered architecture, and try to solve the issue of the layered architecture.

* [Hexagonal (a.k.a. Ports and Adapters) architecture](https://alistair.cockburn.us/hexagonal-architecture/)
* [Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)
* [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)

![The Clean Architecture](https://blog.cleancoder.com/uncle-bob/images/2012-08-13-the-clean-architecture/CleanArchitecture.jpg)

They have some minor differences, 
[fundermentally based on the same ideas](https://blog.ploeh.dk/2013/12/03/layers-onions-ports-adapters-its-all-the-same/).
* Application has layers, but unlike layered (n-tier) architecture, layers look like an "onion" (hence the "onion" architecture), instead of stacked.
* Domain model is at the center of the layers.
* Dependencies only direct inwards. Inner layers don not know about outer layers.
* This can be done by [dependency inversion](https://en.wikipedia.org/wiki/Dependency_inversion_principle).

These architectural patterns become popular along with Domain Driven Design and Microservice architecture, 
because [these three are aligned very well altogether](https://www.linkedin.com/pulse/ddd-microservices-hexagonal-when-all-comes-together-ataul-mukit/).

## Vertical Slice Architecture

![Vertical Slices](https://www.milanjovanovic.tech/blogs/mnw_062/vertical_slice_architecture.png?imwidth=1920)

* https://www.jimmybogard.com/vertical-slice-architecture/
* https://www.milanjovanovic.tech/blog/vertical-slice-architecture
* https://www.youtube.com/watch?v=SUiWfhAhgQw

## Screaming Architecture

[Screaming architecture](https://blog.cleancoder.com/uncle-bob/2011/09/30/Screaming-Architecture.html) is a term coined by Robert C. Martin (Uncle Bob).
It is more about how to organize the project, and the core idea is that "Your architectures should tell readers about the system, not about the frameworks".

![Screaming Architecture](https://media.licdn.com/dms/image/D5610AQEbW1vGidYdoQ/image-shrink_800/0/1698735896342?e=1701154800&v=beta&t=IS02CoCooRNJ53pl-J2yM69nI9PgPNYnJcAydVbKVo8)

Here are related articles regarding code organization: 
* [How to organize your code?](https://kislayverma.com/programming/how-to-organize-your-code/)
* [Package by Feature, not by Layer](https://medium.com/expedia-group-tech/package-by-feature-not-by-layer-5ba04a070003)

