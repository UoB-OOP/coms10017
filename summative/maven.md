Maven
=====

This document is only for the interested student and should be seen as information outside the
exercises, it is neither required nor necessary for your courseworks or the unit to understand
details about *Maven*. Knowing how to compile and run tests, and executing the application as
explained in the exercise task is sufficient. This document will introduce you a bit deeper to the
build tool *Maven* purely for interest and give you a few more few tips on using it.

## Introduction

*Maven* is a build system which takes care of the dependency management, software assembly, and test
reports.

One of the core philosophy in *Maven* is
[convention over configuration](https://en.wikipedia.org/wiki/Convention_over_configuration).

Per [convention](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)
, Maven projects uses a very specific directory structure:

    ├───.gitignore - ignore files for Git
    ├───.mvn - Maven wrapper binaries
    ├───mvnw - Maven wrapper for *nix
    ├───mvnw.cmd - Maven wrapper for windows
    ├───pom.xml - Maven "Project Object Mode", or build configuration
    ├───README.md - this document
    └───src - source directory, contains all source file
        ├───main - application sources
        │   ├───java - java source files
        │   └───resources - resources needed by other source files
        ├───site - site/report generation configuration
        └───test - test sources
            ├───java - java test sources
            └───resources - resources needed by tests only

**Note**: Changing the overall directory structure might cause the project to no longer compile.

Notice the `mvnw`, `mvnw.cmd`, and `.mvnw` entries, those are not part of the standard maven
project. Those files are a wrapper files that delegate commands to the real maven executable and in
cases where maven is missing, download and install it. They could be generated using
the [maven-wrapper](https://github.com/takari/maven-wrapper) tool.

## The Project Object Model

Residing in the project root is the `pom.xml` file. This file describes the current project
in [XML](https://en.wikipedia.org/wiki/XML), here's a sample `pom.xml` file:

```xml

<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.mycompany.app</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>

    <name>My Project</name>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.8.2</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

The file is divided into several section:

#### Maven Coordinates

The maven coordinate looks like following:

```xml

<groupId>com.mycompany.app</groupId><artifactId>my-app</artifactId><version>1.0-SNAPSHOT
</version><packaging>jar</packaging>
```

It is used for others to find your project or for you to reference your own projects.

* `groupId` - a name to identify which group this package is from. By convention, it should be the
  root Java package name of the project.
* `artifactId` - the project name but without spaces or spacial characters.
* `version` - the version number of the project, can be any arbitrary string

#### Dependencies

Maven projects can include other projects as a dependency, for example, we can
include [JUnit](http://junit.org/junit4/) as our dependency:

```xml

<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.8.2</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

All the required class/resources for JUnit will be downloaded and be ready to use in our project.
Maven will also download additional dependencies that JUnit itself requires.

You can search for projects to use on sites such as these:
places:

* [The Central Repository](http://search.maven.org/)
* [mvnrepository](https://mvnrepository.com/)

There are other root level tags that specify build plugins and reports, you read more about them
[here](https://maven.apache.org/pom.html)

## Setup a project for development

Go the the project root(the directory where `pom.xml` resides) and type:

    Linux/OSX:   ./mvnw clean compile javadoc:javadoc
    Windows:     mvnw clean compile javadoc:javadoc

**Note**: On Unix based systems, you might need to make `mvnw`
executable (i.e. `chmod +x mvnw`)

The end of the output should looks something like this:

    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESS
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 42 s
    [INFO] Finished at: 1970-01-01T00:00:00Z
    [INFO] Final Memory: 42M/420M
    [INFO] ------------------------------------------------------------------------

If you get a `BUILD FAILURE`, that means the project failed to complete some of the specified tasks.

The command might take a bit to complete so be patient. You will also need a working internet
connection as Maven downloads project dependencies on the web.

The command is doing 3 separate things in order,

1. `clean` makes sure the project directory is clean
2. `compile` compiles the project and stops if any error is found
3. `javadoc:javadoc` generates javadoc documentations in the
   `target/site/apidocs` directory.

You can learn more about those tasks
[here](https://maven.apache.org/guides/getting-started/index.html)

Now that you have the project setup, you can start reading the generated javadocs. The javadocs are
located in the`target/site/apidocs`
directory, open `index.html` with your web browser and look around. The website contains the
following:

* A list of packages on the top left frame
* A list of classes on the bottom left frame
* Description on the right frame

Is is recommended that you reference the generated Javadoc for a smoother development experience.

The project's main source files are located in `src/main/java` and organised in directories
according to the package name, for example
`a.b.c.d.MyClass` is a file located at `a/b/c/d/MyClass.java`.

The tests are located in `src/test/java` and organised in the same package name to directory
pattern.

## Running unit tests

To run all unit tests, type:

    Linux/OSX:   ./mvnw clean test
    Windows:     mvnw clean test

If all unit tests pass, you should get a `[INFO] BUILD SUCCESS` at the end of the output.

If some tests failed, the result should look something like this:

    Results :
    ....
    Failed tests: ...
    Tests in error: ....
    Tests run: ?, Failures: ?, Errors: ?, Skipped: ?

    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD FAILURE
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 42 s
    [INFO] Finished at: 1970-01-01T00:00:00Z
    [INFO] Final Memory: 42M/420M
    [INFO] ------------------------------------------------------------------------
    [ERROR] Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.19.1:test (default-test) on project my-project: There are test failures.


