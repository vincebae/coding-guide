# Java Best Practices
* [Prefer Immutable Objects and Avoid Setters](#Prefer-Immutable-Objects-and-Avoid-Setters)
* [Prefer Optional for Nullable Objects](#Prefer-Optional-for-Nullable-Objects)
* [Prefer Constructor Injection and Use DI for Unit Tests](#Prefer-Constructor-Injection-and-Use-DI-for-Unit-Tests)
* [Use Try with Resources](#Use-Try-with-Resources)
## Prefer Immutable Objects and Avoid Setters

Encapsulation is one of four principles of object-oriented programming.
Providing setters for all member variables is the easiest way to violate this principle.
Setters should be added only when they are really needed. 

Making a class immutable is even a better approach in most cases.
Immutable objects provide thread safety, protection from hidden side effects and accidental modification and other benefits,
so they help to write codes with better readability and less bugs. 

Java keeps adding support for immutable objects like new date/time API, record types or immutable collections for these reasons.
For Java versions that don't support record types yet, guava immutable collection library is very useful to create immutable collections.

#### Reference

* [Immutable in Java](https://www.leadingagile.com/2018/03/immutable-in-java/)
* [Why is Java making so many things immutable?](https://blogs.oracle.com/javamagazine/post/java-immutable-objects-strings-date-time-records)


## Prefer Optional for Nullable Objects

```NullPointerException``` is probably one of the most dreaded errors in Java.
Annotations like ```@Nullable``` and ```@Nonnull``` can be used to reduce the mistakes when dealing with ```null```,
but ```Optional``` is usually a better way to handle the objects that can be ```null```,
especially with rich fluent APIs like ```map()```, ```orElse()``` and ```ifPresent()```.

However, ```Optional``` also should be used with some caution, obviously. Especially,
* ```null``` must not be assigned to Optional. Assign ```Optional.empty()``` instead.
* ```optionalInstance.get()``` must be called when it is guaranteed to have a value.
* ```Optional``` is also an object, and it can degrade performance if created when not needed. For example,
```
// Avoid:
String str = Optional.ofNullable(someString).orElse("defaultValue");

// Prefer:
String str = someString != null ? someString : "defaultValue";

// Avoid:
Optional<SomeClass> someOptional = Optional.ofNullable(someInstance);
if (someOptional.isPresent()) {
    // Do something with someOptional.get()
}

// Also avoid:
Optional.ofNullable(someInstance)
    .ifPresent(a -> { /* Do something with a */ });

// Prefer:
if (someInstance != null) {
    // Do something with someInstance
}
```

#### References

* [Better null-handling with Java Optionals](https://belief-driven-design.com/better-null-handling-with-java-optionals-da974529bae/)
* [26 Reasons Why Using Optional Correctly Is Not Optional](https://dzone.com/articles/using-optional-correctly-is-not-optional)


## Prefer Constructor Injection and Use DI for Unit Tests

Spring framework is an application platform that can make it easier to develop complicated enterprise Java applications.
At its core, Spring framework is based on a dependency injection container. 
Spring provides three ways for injection: constructor, field or setter.
Among those three, constructor injection has clear benefit to other two methods:
* Construction injection is the only way for final class variables.
* Testing is easier.
* Easier to read and maintain because injection is only done in a single point.

There are some rare cases where field or setter injection needs to be used e.g.

* When libraries require no-arg constructor.
* In order to avoid the circular dependencies (Note that circular dependency is usually a code smell itself.)

For those cases, the reason to use field or setter injection needs to be well documented and constructor injection should be used for all other cases.

There are other frameworks and libraries for dependency injection, e.g. Guice, Dagger, and these principles apply similarily.

One of the biggest advantages of using dependency injection is that it makes unit tests easier.
As the name suggests, with dependency injection, dependencies are injected when an object is created instead of being tightly coupled with the object.
Therefore, those dependencies can be easily mocked out during the unit tests.

“Time” and “Date” are great examples.
In Java, time and date are generated by the system clock by default.
However, we can explicitly use a clock instance to be used when generating time and date.
By injecting a clock instance, we can test various time and date cases not restricted to just the system time.

#### References

* [Unit testing and dependency injection](https://coderstower.com/2019/10/07/unit-testing-and-dependency-injection/)
* [Unit testing classes that depend on time](https://blog.indrek.io/articles/unit-testing-classes-that-depend-on-time/)
* [You should stop using Spring @Autowired](https://dev.to/felixcoutinho/you-should-stop-using-spring-autowired-p8i)


## Use Try with Resources 

There are cases where we need to deal with the resources that need to be closed properly after use, like files or database connections.
When they are not properly released, it can lead to memory leaks and/or performance issues. 

The traditional way to deal with resources is try-catch-finally, where resources are closed in finally block.
However Java 7 introduced a “try-with-resources feature” and it should be preferred instead whenever possible.
For the detailed information about try-with-resources, refer to the link below.

#### References

* [Java try with resource](https://www.baeldung.com/java-try-with-resources)
