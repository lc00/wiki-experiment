* Combine objects with either inheritance (is-a) or composition (has-a)
* Separate interface from implementation
    * Change to implementation should not change any code that depends on it
* Operator overloading allows an operator to have more than use (eg. + is addition and string concatenation). Avoid, this is confusing.
* Muliple inheritance (C++) is also confusing
* Accessors: Getters & Setters
    * Methods allow you to check for permission, etc.
* You can wrap non-portable or legacy code in a wrapper to change its interface
* Contracts are abstract classes and interfaces
* Abstract classes can include code that can be inherited, interfaces cannot
    * You can also use multiple interfaces, but only inherit from one abstract class

## UML

* Empty arrow: Is-A
* Diamond: Has-A, Aggregation
* Solid Line: Has-A, Association
* Dashed line: Interface

## Inheritance

* May be based on behaviors (`BarkingDog` / `YodelingDog` then breed)
* May include cardinatlity
* Weakens encapsulation because changes in superclasses can affect the behavior of subclasses that depend on it
* Classical inheritance means that you're actually working with a parent class that has all of the state and behavior of its children

## Composition

* Composition makes parts interchangeable
* Aggregation & Association
* Aggregation means an object composed of other objects
* Association means an object uses another object
* If an association is optional, you need to check for null

## Encapsulation

* Separating interface & implementation
* Prevent access to properties directly
* Combine behaviors & state

## Abstraction

* Find the common behavior in classes and abstract it out
* Interfaces should be more abstract than concrete
* Multiple database implementations the have the same interface

## Polymorphism

* Calling the same method on different objects with different implementations in subclasses
* A `render` method on different shapes

## Design

* Start by turning the requirements into interfaces- what do users need to interact with?
* Overloading methods: Different signatures
    * You can have multiple constructors with different signatures
* Always design the smallest interface you can
* Abstract out non-portable code (platform-specific)
* Classes should be responsible for themselves
* Highly-coupled classes mean that a change in the system means a change in the implementation

### Design Patterns

A pattern is a:

* Name
* Problem
* Solution
* Consequences

#### Creational Patterns

* Abstract factory
* Builder
* Factory method
* Prototype
* Singleton - Global state

#### Structural Patterns

* Adapter - Wraps a class to give it a new interface
* Bridge
* Composite
* Decorator
* Facade
* Flyweight
* Proxy

#### Behavioral Patterns

* Chain of response
* Command
* Interpreter
* Iterator - Abstract out a loop
* Mediator
* Memento
* Observer
* State
* Strategy
* Template Method
* Visitor

## Construtors

* Constructors should put the object in an intial, safe state
* Initialize your attributes in the constructor
* Constructors don't have returns types, everything else must
* Possible destructor if things need to be disconnected

### How Objects are constructed

* `new` allocates memory
* Superclass's constructor is called
* Each attribute of the superclass is initialized
* Class's constructor is called

## Attributes

* Local attributes: Part of methods
* Object attributes: Part of an instance
* Class attributes: Static attributes shared by all instances

## Error Handling

* Try blocks can have multiple catches for different cases

## Serializing

* Sending a serialized object is called marshaling
