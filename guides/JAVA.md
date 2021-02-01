Java Quick Reference
====


<!-- toc -->

- [Java](#java)
    - [Terminology](#terminology)
        - [Classpath](#classpath)
    - [Language features](#language-features)
        - [Inheritance](#inheritance)
        - [Generics](#generics)
            - [Type inference](#type-inference)
            - [Type erasure](#type-erasure)
            - [Wildcards](#wildcards)
            - [Intersection types](#intersection-types)
        - [Covariance and Contravariance](#covariance-and-contravariance)
        - [Exceptions](#exceptions)
            - [Unchecked exception](#unchecked-exception)
            - [Checked exception](#checked-exception)
        - [Varargs](#varargs)
        - [Initialisers](#initialisers)
            - [Instance initialisers](#instance-initialisers)
            - [Static initialisers](#static-initialisers)
        - [Anonymous class](#anonymous-class)
        - [Annotations](#annotations)
        - [Static imports](#static-imports)
        - [Java 8+](#java-8)
            - [Lambda expressions](#lambda-expressions)
            - [Method reference](#method-reference)
            - [Default methods](#default-methods)
    - [Libraries and API](#libraries-and-api)
        - [Java 8+ Stream](#java-8-stream)
        - [Java 8+ Optional](#java-8-optional)

<!-- tocstop -->

## Terminology

### Classpath

The classpath contains paths to user defined classes. If a project has library dependencies, the
classpath should contain paths to those libraries.

## Language features

Below are a some of the language features used in the worksheets and coursework.

### Inheritance

One of the fundamental concepts of Object Oriented programming. Given some class `Animal`

```java

class Animal {
	// some properties
}

```

We could create another class that inherits properties of `Animal` :

```java
class Dog extends Animal {
	// some more properties
}
```

Methods in the base class `Animal` could be overridden to alter behavior.

Java also supports abstract classes. An abstract class could not be instantiated directly. Below is
an example of abstract class by making
`Animal` abstract and `Dog` a concrete implementation of `Animal`:

```java
abstract class Animal {
}

class Dog extends Animal {
}

// to instantiate:
    new Animal(); // error
		    new Dog(); // ok

```

### Generics

Generics are supported since Java 5. The simplest form looks like this:

```java
class Pair<L, R> {
	final L left;
	final R right;

	//...
	Pair(L l, R r) {
		this.left = l;
		this.right = r;
	}
	//...
}
```

The `Pair<L,R>` class can be instantiated by:

```java
Pair<Integer, String> pair=new Pair<Integer, String>(42,"foo");
``` 

The right hand side generic parameter could be inferred by the compiler so they can be reduced
to `new Pair<>(...)`.

Generics are also supported in interfaces and static methods, below is an example of generics in
static method:

```java
    //unchecked
static<T> T create(Object object){return(T)object;} 
```

#### Type inference

Java supports simple type inference since Java 7.

Without type inference:

```java
List<String> strings=new ArrayList<String>();
```

With type inference:

```java
List<String> strings=new ArrayList<>();
```

The `<>` symbol is known as the diamond operator. The operator could be used with any parameterised
type, for example:

```java
Map<String, Map<Long, Pair<Double, Double>>>map=new HashMap<>();
```

Type inference also works with static methods:

```java
List<String> strings=Arrays.asList("foo","bar");
```

Which is actually:

```java
List<String> strings=Arrays.<String>asList("foo","bar");
```

This usage is called the type witness. It is only required when the compiler does not have
sufficient information to deduce the target type.

The compiler might not be able to deduce the target type when:

* Instantiating an anonymous class (no longer the case in Java 9)
* Method returns a raw type

#### Type erasure

Generics in Java are non-reifiable, meaning that generics are removed at compile time.

Due to this limitation, the following code is illegal:

```java
static<T> T createMyObject(){return new T();} // illegal
static<T> T[]createMyArray(){return new T[42];} // illegal
```

In the above examples, `T` gets erased and effectively becomes
`java.lang.Object`. The type information gets lost so during runtime the JVM could not decide which
type to instantiate. There are tricks around these restrictions but those are out of the scope of
this document.

Type erasure also forbids method overloading with generic types in some cases:

```java
static void doIt(List<String> args){}
static void doIt(List<Integer> args){} // illegal
```

Both method has the same erasure so overload resolution fails.

#### Wildcards

Java supports wildcards through bounds. For example, the following method accepts a `List` of any
type:

```java
static void doIt(List<?> items){}
```

We could also limit the accepted type to some subtype(upper bound) or supertype(lower bound):

```java
static void doA(List<?extends Animal> items){}
static void doB(List<? super Dog>items){}
```

This is called use-site variance as the use-site of the methods decide whether the parameters
conform the the methods's generic wildcard expression.

#### Intersection types

Java have limited support of intersection types. For example:

```java
static<T extends A & B> void foo(T t){}
```

The method `foo` restricts the type of `T` to some type that implements both interface `A` and `B`.

### Covariance and Contravariance

For simple inheritance, Java methods has the following properties:

* Parameters types - contravariant
* Return type - covariant

For generics, the relationship could be illustrated in form of a graph:

```
Given:
    A<E> <- A'<E>
    B <- B'
      
        A<? extends B>
      /  |
     /   |
   A<B>  |
    |   A'<? extends B>    
    |   / 
    |  /
  A'<B>
   
```

All edges points upward.

### Exceptions

Java supports two types of exceptions: checked and unchecked.

#### Unchecked exception

Unchecked exceptions does not need to be surrounded by try-catch blocks. For example:

```java
throw new RuntimeException("Assertion error!");
```

The program crashes with a stacktrace to the given exception.

#### Checked exception

Checked exceptions must be surrounded by try-catch blocks. For example:

<!-- @formatter:off-->
```java

try{
	throw new IOException();
}catch(Exception e){
	throw new RuntimeException(e);
}
```
<!-- @formatter:on-->

The above example also showcases a common usage of rethrowing exception as unchecked ones in case
the original exception is not recoverable.

### Varargs

Java supports variadic arguments, or parameters that take an arbitrary length argument with the same
type.

```java
void foo(String...strings){...}
```

The resulting type of `strings` is simply an array of `String`,
`String[]`. Varargs can only be used once and must be the last argument in a method signature. For
example:

<!-- @formatter:off-->
```java
void foo(int a,int b,String...strings){} // legal
void bar(String...strings,int a,int b){} // illegal
```
<!-- @formatter:on-->

Varargs could be useful at limiting ways to construct a object. Given:

```java
class Foo {
	Foo(int first, int second, int... rest) { /*...*/ }
}
```

The constructor `Foo` effectively requires n+2 arguments to instantiate

### Initialisers

Other than constructors, Java supports initialisers for instantiation:

#### Instance initialisers

For example

```java
class Foo {
	int foo;

	{
		foo = 42;
	}
}
```

A common use case is the double brace initialisation of collection types:
<!-- @formatter:off-->

```java
new ArrayList<Integer>(){{
	add(1);
	add(2);
}};
```

<!-- @formatter:on-->

NOTE: the use of double brace initialisation is debatable as the instantiated `ArrayList` is not
an `ArrayList` itself, but an anonymous class that extends `ArrayList`

#### Static initialisers

```java
class Foo {
	static final String constant;

	static {
		constant = "bar";
	}
}
```

### Anonymous class

Java supports inline classes that loosely captures the notion of closures, for example:

```java
List<String> strings=new ArrayList<>(){};
```

`strings` is now some anonymous class that extends `ArrayList` . The class can also capture
effectively-final variables if used within a method call, for example

```java
class Main {
	interface Action<T> {
		T doIt(T source);
	}

	public static final void main(String[] args) {
		final int value = 10;
		Action<Integer> addValue = new Action<Integer>() {
			@Override
			public Integer doIt(Integer source) {
				return source + value;
			}
		};
		addValue.doIt(10); // == 20;
	}
}
```

### Annotations

Java supports annotations as a facility for metaprogramming. Annotations may be read at runtime or
compile time to generate code.

The simplest form can be seen while overriding methods:

```java
public class Foo {
	@Override
	public String toString() {
		return "foo";
	}
}
```

Where the `@Override` annotation notifies the compiler that the method must override a method.

<!--TODO more examples-->

### Static imports

To reduce verbosity, Java allows import of static instances. For example:

```java
List<Integer> list=Arrays.asList(1,2,3);
```

Can be rewritten as:

```java
import static java.util.Arrays.asList;
// ...
List<Integer> list=asList(1,2,3);
```

Note that this only works when method names do not clash.

### Java 8+

Java 8 introduced syntax support for functional programming as well as backwards compatible
interface evolution.

#### Lambda expressions

Starting from Java 8, syntactic sugar for anonymous class has been introduced to improve
readability. Given the anonymous class with its definition:

<!-- @formatter:off-->
```java
interface Action<T> {
	T doIt(T source);
}
Action<Integer> increment = new Action<Integer>() {
	@Override
    public Integer doIt(Integer source) {
		return source + 1;
	}
}
```
<!-- @formatter:on-->

`increment` can be rewritten as:

```java
Action<Integer> increment=source->source+1;
```

#### Method reference

To further reduce boilerplate, lambda expressions that take the exact same parameter could be
further simplified. Given a definition and some prefix function:

<!-- @formatter:off-->
```java
interface Action<T> {
	T doIt(T source);
}
Action<String> prefixFoo = x -> "Foo".concat(x);
```
<!-- @formatter:on-->

`prefixFoo` can be rewritten as:

```java
    Action<String> prefixFoo="Foo"::concat;
```

#### Default methods

Interfaces in Java 8 now supports methods with default implementations. For example:

```java
interface Foo {
	void doIt();

	default void doItTwice() {
		doIt();
		doIt();
	}
}
```

This is particularly useful for adding features to old interfaces without breaking binary
compatibility. Notable uses include
`Collection#stream` and `Collection#forEach`.

## Libraries and API

Java has an active community and an abundance of third-party libraries that would shorten
development time. Below is a list of commonly used libraries.

* [Guava](https://github.com/google/guava) - common utilities
* [JUnit](http://junit.org/junit4/) - testing framework
* [Mockito](http://site.mockito.org/)- mocking framework
* [Apache Commons](https://commons.apache.org/) - suite of reusable tasks

This list is by no means representative as there are many domain specific libraries as well.

### Java 8+ Stream

Java 8+ introduced Streams for lazy processing. Previously tedious task such as filtering collection
elements are now easy and safe.

For example:
<!-- @formatter:off-->

```java
List<Integer> ints=Arrays.asList(1,2,3,4,5);

//Java 7:
List<Integer> result=new ArrayList<>();
for(Integer value : ints){
    if(value%2) result.add(value);
}

//Java 8:
List<Integer> result=ints.stream().filter(i->i%2).collect(toList());


```
<!-- @formatter:on-->

### Java 8+ Optional

Java 8+ provided a simple utility class called `Optional` to safely navigate around null values. For
example:

<!-- @formatter:off-->
```java

class Foo {
	String bar() {
		return null;
	}
}

Foo badFoo = null;
// Java 7
int barLength = 0;
if(badFoo!=null){
	String bar=badFoo.bar();
	if(bar!=null){
		barLength=bar.length();
	}
}

// Java 8
int barLength=Optional.ofNullable(badFoo)
    .map(Foo::bar)
    .map(String::length)
    .orElse(0);

```
<!-- @formatter:on-->
