Maven
=====

## Maven cheat sheet

Frequently used commands:

 - Clean - `mvnw clean` (deletes compiled classes, safe to do anytime)
 - Compile - `mvnw clean compile`
 - Test - `mvnw clean test`
 - Run single test class -  `mvnw test -Dtest=<class>`
 - Run single test -  `mvnw test -Dtest=<class>#<method>*`
 - Start program - `mvnw clean compile exec:java`

Flags:

 - `-q` - quiet output
 - `-e` - show detailed stacktrace for maven internals
 - `-i` - verbose output
 - `-Dwerror=true|false` - fail on warning or not
 - `-DskipTests` - skip unit tests

