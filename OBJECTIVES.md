Objectives
==========

##CW-MODEL & CW-OXO

###Constructor

The constructor of CW-MODEL teaches the following:

####Using language features to restrict user input

The constructor of the skeleton looks like the following:

```java
	public ScotlandYardModel(List<Boolean> rounds, Graph<Integer, Transport> graph,
			PlayerConfiguration mrX, PlayerConfiguration firstDetective,
			PlayerConfiguration... restOfTheDetectives)
```

The intent of splitting the `PlayerConfiguration` argument into 3 is so
that the client of the constructor would not supply bad parameters.
In the example above, we essentially limited the input of 
`PlayerConfiguration` to be exactly 1 Mr.X and 1 or more Detectives.

To illustrate, the following input is valid:
```java 
    new ScotlandYardModel(rounds, graph, mrX, blue);
    new ScotlandYardModel(rounds, graph, mrX, blue, red);
    new ScotlandYardModel(rounds, graph, mrX, blue, red, green);
```
Where as the following does not compile:
```java 
    new ScotlandYardModel(rounds, graph);
    new ScotlandYardModel(rounds, graph, blue);
    new ScotlandYardModel(rounds, graph, mrX);
```

If we were to use `PlayerConfiguration... configs`, then the client 
could leave the parameter empty and the program would crash at runtime.


####Defensive programming

The constructor of both CW-OXO and CW-MODEL must validate all input
parameters and throw exceptions
when they are not valid.

Test suite `uk.ac.bris.cs.scotlandyard.model.ModelCreationTest` tests 
whether the model is defensive in that all parameters are validated. 


###Immutable object access

Immutable objects prevent clients of a class from corrupting the state.
In the model, all methods that return a collection must be an immutable. 
For example, the `List<Colour>` returned from 
`uk.ac.bris.cs.scotlandyard.model.ScotlandYardModel.getPlayers`
throws an exception upon modification.

Test suite `uk.ac.bris.cs.scotlandyard.model.ModelCreationTest` tests 
whether returned collections are immutable.


###Fail early

Methods such as `uk.ac.bris.cs.scotlandyard.model.ScotlandYardModel.registerSpectator`
would throw exceptions when the given argument breaks the contract. 

Test suite `uk.ac.bris.cs.scotlandyard.model.ModelSpectatorTest`,
`uk.ac.bris.cs.scotlandyard.model.ModelRoundTest` tests whether bad 
inputs will an appropriate exception.


###Unit testing

CW-OXO intentionally left out a few unit tests around the
`registerSpectator` functionality, those could be uses as
unit testing practices.

###Functional programming

Both CW-MODEL and CW-OXO contains two versions of the reference
model implementation. One is the Java 7 model that uses imperative
programming, the other model uses functional programming
features introduced in Java 8.

###Patterns

Several design patterns are used on the mode:

####Observers

The spectator feature of the model uses the observer pattern

####Visitors

`Move` and subcasses such as `TicketMove` have visitors built in. 

####Builder

`PlayerConfiguration` has a thread safe builder class to build
instances of `PlayerConfiguration`

####Inversion of control

Players only need to implement an interface to be injected into the 
model via the constructor. 


##CW-AI
 
###Patterns

Several design patterns are used on the module:

####Factories

AIs have to implement the `PlayerFactory` interface.

 
