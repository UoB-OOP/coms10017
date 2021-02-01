# Common issues & FAQ

## General notes

1. We **only support Java 11**. If you use Java 8/9/10, you may encounter unexpected issues and _we
   cannot help you with them_. If you've previously installed Java 8/9/10, we recommend that you _
   uninstall Java 8/9/10 and install **only** Java 11_.
   Read [Uninstalling Java](guides/SETUP.md#uninstalling-other-java-versions) if you need a hint on
   where to start.
2. For debugging, use `System.out.println(...)` liberally. Make sure to make it easily spottable,
   e.g. `">>>>>> roundNum" + round`, otherwise it might get lost in maven's long output.
3. For JUnit, a test `Failure` is not the same as `Error`. If a test fails due to some unexpected
   exception, then it's an error that has nothing to do with the actual test.
4. _Please_ read the course descriptions _carefully_. Most of the details you need _are there_, you
   just need to take the time to find them and understand them.

## Common issues

* During test/runtime:`RuntimeException: Implement me`<br />
  This is placeholder for you to implement some code. You need to remove
  the `throw new RuntimeException("Implement me");` statement.
* On
  Windows, `'javac' is not recognized as an internal or external command, operable program or batch file.` <br />
  The `PATH` environment variable is not set up to contain your java installation. Follow the
  instructions in [Setup on Windows](guides/SETUP.md#windows).
* `javac`:`cannot find symbol...`<br />
  Compilation error, probably syntax related. Or possibly the correct `JAVA_HOME` environment
  variable is not set, see the next entry for more details.
* `mvnw`:`Error: JAVA_HOME is not defined correctly; We cannot execute ….`<br />
  The `export JAVA_HOME=…` step is only meant for MVB2.11 Linux lab machines **only**.
  Run `unset JAVA_HOME` to undo this.
* `./mvnw`:`/bin/bash^M: bad interpreter…`<br />
  The `mvnw` script is broken due to Windows line endings. On Linux, do `sed -i -e 's/\r$//' mvnw`
  to fix `mwnv`. macOS users can try `dos2unix`.
* `mvnw`:`The goal you specified requires a project to execute but there is no POM in this directory`<br />
  The `mvnw` command should be executed from the project root (where `pom.xml` is located).
* `mvnw`:`java.lang.UnsupportedClassVersionError:... Unsupported major.minor version 5...`<br />
  Maven wrapper needs Java 8 to work, check that the correct `JAVA_HOME` is set. If this happens on
  a Mac, make sure that `JAVA_HOME` is **not** pointing to the system-bundled Java 6.
* `mvnw`: Compilation is failing because of warning messages being treated as errors. <br />
  Ideally, you should deal with the warnings so that they don't come up any more.
  Read [the Maven page](guides/MAVEN.md) for more info.
* `mvnw`: `[WARNING] bootstrap class path not set in conjunction with -source 1.8` <br />
  You are using the wrong version of Java -- you need to use Java 11!
  Read [the Setup page](guides/SETUP.md) for instructions on how to uninstall the wrong versions and
  install the correct one.

## FAQ

**Q**: How do I know what caused a test to fail? What is a stacktrace? <br />
**A**: A stacktrace tells you which method threw an exception and the path (call trace) that leads
up to the exception. Most tests will print some sort of stacktrace in Maven's output (NOTE: adding
the `-e` flag only prints stacktrace for maven internals, not the actual test). If you are still
unsure, [this](https://www.reddit.com/r/javahelp/wiki/learn_to_help_yourself) tutorial may be
helpful.

**Q**: Can I have multiple `return`s in a method? <br />
**A**: Yes, early returns will "short-circuit" and finish the method execution.

**Q**: I have nested `while`/`for` loops and I want to break out of them, what should I do? <br />
**A**: Refactor the nested loop into a separate method so that you can return early.

**Q**: Can I use labels in `while`/`for` loops? <br />
**A**: Yes but it is not encourage nor required for any of the coursework.

**Q**: How does `<test method>` work? <br />
**A**: Read the test's method name, and then quickly skim the code (it should read like English). If
you are still not sure, consult one of the TAs or ask on the forum.

**Q**: Why can't I find the implementation for `<some interface>`? <br />
**A**: Not all interfaces have implementations, read lecture slides.

**Q**: Why is the source nested so deep? for
example:`src\test\java\uk\ac\bris\cs\scotlandyard\...` <br />
**A**: That's how Java packages work, live with it.

**Q**: Can I use lambdas/streams/functional things/external library? <br />
**A**: Yes.

**Q**: Why is `<some method>` undocumented? <br />
**A**: Not everything requires documentation (**do report this as it could be an oversight**).

**Q**: Can I modify the tests? <br />
**A**: No.

**Q**: Can I modify any other files in the coursework? <br />
**A**: Yes, but it is your responsibility to make sure tests still pass (without modifying them) and
the project still compiles.

**Q**: Do I have to use git? <br />
**A**: No, you may use any version control software you see fit.

**Q**: How do I initialise/commit/push/pull/merge/revert/... using git? <br />
**A**: The [Atlassian git tutorials](https://www.atlassian.com/git/tutorials) explain most common
operations. A quick Google search, e.g. `git how to <operation>`, should also return plenty of
useful resources.

**Q**: I am getting an error that I haven't seen before. What do I do? <br />
**A**: Read the error message _carefully_. It will most likely tell you what's happening and give a
hint about where the error originated. Start by investigating there and seeing if you can spot any
issues.

**Q**: I am seeing an error message that I don't understand. What should I do? <br />
**A**:
Use [your](https://www.google.co.uk) [favourite](https://duckduckgo.com/) [search](https://www.bing.com/) [engine](https://uk.search.yahoo.com/)
to search for the error message as it comes up. Using `"double quotes"` around your search term will
make sure the search engine treats it as one single term rather than splitting it up into words. If
you get many results, try narrowing things down by adding some keywords related to your problem,
e.g. mac/ubuntu/windows, git/java/vim, or eclipse/intellij/atom.

**Q**: I have not found any help online and I don't think anyone has encountered this problem
before. What else can I do? <br />
**A**: Try a few variations on your search engine query, such as rephrasing your issue or pasting a
different part of the error message. If you still cannot find any help, post on the forum, giving a
detailed description of the problem and showing the steps to reproduce your issue.

**Q**: Can I use functional programming concepts (i.e `map`, `flatMap`, etc) in the
coursework? <br />
**A**:So the course is called Object Oriented Programming so naturally we want students to learn
about OOP and not functional programming. That said, functional programming in Java 8 and above
mostly simplifies imperative bits of your program and doesn't reduce OOP as the task has a clear
interface that you have to implement. Think of it this way:

By specification, you have to call the `makeMove` method of the current player with a view of the
model. Successfully implementing this requires you to understand that the model is an instance that
implements the view interface and that your model interacts with multiple instances of the player
type by calling methods(sending messages). If you can explain that clearly then you have achieved
the learning outcome. Tasks such as finding the current player or signalling multiple spectator of
some events could be done either declaratively through FP or imperatively by iterating through a
collection of players/spectators. Because in Java everything is an object (excluding primitives),
whatever you pick here, you are technically doing OOP so if you understand how the FP code you wrote
works in terms of OOP, I don't see why you shouldn't use it. If you do use FP, be prepared to
justify why it is better than the other approaches in your case; the ability to do so will also land
you some credits.

