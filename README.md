Panda2 quick reference
===================================

## Maven cheat sheet

Tasks:

 - Clean - delete binaries
 - Compile - compiles the entire project
 - Test - run all unit tests (compiles project if not already compiled)

Frequently used commands:

 - Clean - `mvnw clean`
 - Compile - `mvnw clean compile`
 - Test - `mvnw clean test`
 - Run single test class -  `mvnw test -Dtest=<class>`
 - Run single test -  `mvnw test -Dtest=<class>#<method>*`
 - Start program - `mvnw clean compile exec:java`

Flags:

 - `-q` - quiet output
 - `-e` - show detailed stacktrace for maven internals
 - `-i` - verbose output
 - `-DskipTests` - skip unit tests

## Common issues

* During test/runtime:`RuntimeException: Implement me`  
      Student didn't remove the `throw new RuntimeException("Implement me");` statement
* mvnw:`Error: JAVA_HOME is not defined correctly; We cannot execute ….`  
      The `export JAVA_HOME=…` step is only meant for lab machines ONLY; students don't usually read  
      Run: `unset JAVA_HOME` to undo this
* ./mvnw:`/bin/bash^M: bad interpreter…`  
      The `mvnw` executable is broken; if on Linux, do `sed -i -e 's/\r$//' mvnw`; OSX users can try `dos2unix`
* mvnw:`The goal you specified requires a project to execute but there is no POM in this directory`  
      The `mvnw`  command should be executed from the project root(where `pom.xml` resides)
* javac:`cannot find symbol...`  
      Compilation error, probably syntax related


## Language questions

Q: Can I have multiple returns in a method?  
A: Yes, early returns will "short-circuit" and finish the method execution

Q: I have nested while/for loops and I want to break out of them, what should I do?  
A: Refactor so that you don't have nested loop

Q: Can I use labels in while/for loops?  
A: No (there are legitimate uses but it is not encourage nor required for this coursework)

Q: How does `<insert test method>` work?  
A: Read the test's method name, and then quickly skim the code(it should read like English)

Q: Why does `<insert IDE>` not work?  
A: We don't teach IDEs, if you want to use one you'll have to spend time learning yourself

Q: Why can't I find the implementation for `<some interface>`?  
A: Not all interfaces have implementations, read lecture slides

Q: Why is the source nested so deep? for example:`src\test\java\uk\ac\bris\cs\scotlandyard\...`  
A: That's how Java packages work, live with it

Q: Can I use lambdas/streams/functional stuff/external library?  
A: Yes


## General questions

Q: What is `<some class>` and what does it do?  
A: Read the JavaDoc

Q: Why is `<some method>` undocumented?  
A: Not everything requires documentation(**do report this as it could be an oversight**)

Q: Can I delete `<insert random file in project>` file?  
A: Yes(except for test classes), as long as the tests pass

Q: Can I modify the tests?  
A: No

Q: Do I have to use Git?  
A: No

Q: Can I modify the directory structure?  
A: No
