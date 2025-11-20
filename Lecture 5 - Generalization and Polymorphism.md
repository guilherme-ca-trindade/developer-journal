# Generalization and Polymorphism

## Software  design principles

### Cohesion
Definition: cohesion is the degree to which the parts of one component are related to each other
	- E.g. Do all these members make sense/ belong in this class?
		○ Weak cohesion (harder to understand) <-
		○ Strong cohesion (easier to understand) -> (better)

### Coupling
Definition: coupling is the degree to which different components depend on each other
	- How much do different components need to "know" about each other to a function?
	- Analogy: phone charged wired into wall vs plug vs induction
		○ Tight coupling (more interdependent, harder to maintain) <-
		○ Loose coupling (less interdependent, easier to maintain) -> (better)

### Review of OOP principles
	- Abstraction - focusing essential detail; ignoring irrelevant complexity
	- Encapsulation -  exposing an abstraction; hiding implementation detail

## Polymorphism 
(Broad) Definition: Polymorphism is the enabling of uniform interaction for different types
Polymorphism we have already encountered: 
	- Type coercion: automatic conversion between types.
	- Method overloading: same method can handle different types.
	- Operator overloading: + works on Strings and ints, etc.
	- Generic types: a type that can "hold" any other type (e.g. List<String>)

### Subtype polymorphism
…

## A new OOP Principle:
## Generalization
	- Share common details in a broader abstraction
	- It can be useful to analyze the "things" being modelled (types/data/structures) in a program for common state or behavior
	- Reduces code repetition (DRY)
	- Can make programs more maintainable
		○ Don't need to remember to change code in multiple classes.

## Inheritance
	- Think of inheritance as an 'is a' relationship
	- E.g. 
		○ A Student IS A Person
		○ An Instructor IS An Employee
		○ An Instructor IS A Person
		○ An Employee IS A Person

## Generalization Terms
	- Superclass:
	- Subclass:
	- Inherit:

## Inheritance
	- Java classes may have ONLY ONE superclass
		○ Specified using the extends keyword
		○ If not specified, then Object is the superclass


### >>> Protected vs Private
Private can only be use by the class itself, even their subclass can use this method.
Protected, nevertheless, can be used by the class itself or their subclass

### Inheritance and constructors
	- Constructors in an inheritance hierarchy are called in sequence from …
	- The super keyword can be used to call a constructor of the superclass
	- Must be the FIRST statement in a constructor

### Overriding methods
	- It is often useful to have a subclass provide a different implementation of a method than its superclass(es)
		○ E.g. Override the toString method that is defined in the Object class

### Static Types vs Run-Time Types
	- The Static Type…


### Subtype Polymorphism
	- Dynamic method dispatch allows for subtype polymorphism (allowing subtype values to be treated as supertype instance)

--- 
## Understanding Polymorphism with Pokemon:
https://medium.com/@omarfdez92/lets-explore-polymorphism-in-java-using-pokemon-da4c74a9c876
