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
- `-e` - show detailed stacktrace for **maven internals**, this is not what you are looking for if
  you want stacktraces from your program.
- `-i` - verbose output
- `-Dwerror=true|false` - fail on warning or not
- `-DskipTests` - skip unit tests

**Note**: The maven build script we provide is set up to treat warnings as errors by default. This
is to make you aware of potential issues in your code, and ideally you should address the cause of
the warnings before proceeding. If you are absolutely sure you know what you are doing, you can
override this behaviour using the `-Dwerror` flag.

