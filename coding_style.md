# Coding Style
## Code Formatter

Thanks to the modern IDEs, formatting the codes to follow the style guide is just one click away. 
It can be done even without doing anything if the IDE is set to apply the formatter on save. 
Here are some of the popular style guides and code formatters:
* Java
  * [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
  * [Google Java Formatter](https://github.com/google/google-java-format)
  * [IntelliJ Plugin](https://plugins.jetbrains.com/plugin/8527).
* Clojure
  * [cljstyle](https://github.com/greglook/cljstyle)

## Comments and Documentation

Writing comments is a controversial topic. There definitely are good comments and also bad comments. 
Some people argue that comments are essential for good codes, and some regard comments as failures to express ourselves in code. 
Both camps have their points, however, even for the latters, documentation comments for public interfaces (like Javadoc) are considered necessary.
Especially these information should be well-documented in Javadoc for better readability:

* Units e.g. days, seconds  
* Boundary conditions
  * What happens if parameters are null?
  * What happens if collections are empty?
  * Are the ranges inclusive or exclusive?
  * Can it return null? (note: consider using Optional if null value can be returned as discussed below)
* Side effects
  * Can exceptions be thrown? When and what?
  * Can it change internal states of itself?
  * Can it change internal states of parameters?
  * Does it have any output parameters? (note: output params should be avoided as discussed below)
* Thread safety (note: immutable objects are always thread safe)
* How can the data object be used?
  * Only internally?
  * For database access?
  * Over the network?

### References
* [Best practices for writing code comments](https://stackoverflow.blog/2021/12/23/best-practices-for-writing-code-comments/)
* [Don't Write Comments](https://www.youtube.com/watch?v=Bf7vDBBOBUA)

## TODO Comments

TODO comments can be unmanageable if not dealt with in a timely manner. 
When TODO comments are merged to the main branch, it should be explicitly associated with a ticket (either Jira or Github) 
so that it can be tracked and handled in the near future. 
TODO comment with the ticket would be like this:

// TODO(CRO-12345) Fix … when …

// TODO(#123) Fix … when …

