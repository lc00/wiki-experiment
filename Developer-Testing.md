## Programming By Contract

* Assertions, Preconditions, Postconditions
    * Not for user input or critical execution path
    * Use for programmer errors, or incorrect caller behavior
* Throw Exceptions
    * For user input
* Unit Tests
    * Makes it possible to verify contracts
* Static Analysis
    * Compile time, type annotations

## Drivers of Testability

* Pure functions
    * Consistency
    * No side effects
    * No changing another scope
    * No I/O
    * No thrown exceptions
    * No calling by reference
* Reduce the amount of application state
* Reducing temporal coupling (required order)
* Types (make illegal states unrepresentable)
* Domain/Range Ratio (DRR)
    * Higher number means more test cases are needed
    * Reducing DRR with constraints makes it easier to test

## Unit Testing

* Not for hobby projects
* Enables scale
* Forces better design
* Enables change
* Prevents regressions
* Steadies pace of development
* Specifies and documents the code
* Checks for the simple stuff
* State is represented by fixtures
    * Set these up in initializers
        * Initalizers are setup code, especially for multiple tests

### Definition

* Automatable
* Each one tests one thing
* Runs independently
* Doesn't:
    * Talk to the database
    * Use a network
    * Use the file system
    * Require an environmental setup

### Test Names

#### BDD

* "The class should do something"
    * Example: "The calculator should add"
* Encourages fluent syntax: `It("test name here")`

#### TDD

* `UnitOfWork_StateBeingTested_ExpectedBehavior`
    * Example: `ATM_NegativeWithDrawal_FailsWithMessage`

### Structure

#### AAA Tests

1. Arrange (Set things up)
1. Act (Execute code)
1. Assert (Verify condition)

Also called:

* Build / Operate / Check
* Given / When / Then
* Setup / Execute / Verify / Teardown

### Assertions

* Assert for one reason per test
    * Only do multiple assertions if the same failure has multiple parts
* Duplicate things like string contents for clarity instead of using variables
* Fluent assertions: `Assert.that(quantity, Is.EqualTo(10))`
* You can test complex or unique things by sending objects to "reverse engineer" them
* Don't use assertion messages- they're as bad as comments

## What To Test

Look for "Equivalence Partitions" (groups of values that are functionally identical):

* Numbers
    * Zero
    * Negative
    * Postive
    * Integer boundaries
    * Float precision
    * At the boundary edges of each partition
* Strings
    * Empty string
    * String with values
    * Null
    * Different encodings
* Dates
    * Use library and types to ensure format
    * Determine whether you're using the time component of date-time
    * Locale sensitivity
    * 23 and 25 hour days
    * Boundaries edges - Hours, months, years, etc.
        * Try picking 1/31 and then switching to February and back
* Collections
    * Empty
    * One item
    * Many items

### State-Transitions

* States
* Transitions
* Events - Cause transition ("Click button")
* Actions - Result of transitions ("Show screen")

State-transition tests:

* 0-Switch: Individual transitions
* 1-Switch: Pairs of transitions

### Decision Tables

* Have all possible combinations, and what the outcome is
* Good for uncovering weird business rules

## Testing Dependencies

* Dependencies require "seams" in the code to be tested
    * Pass in collaborating objects instead of magically initializing them
    * Make a factory that can be overridden by the testing framework
    * Pass factories into the constructor
* System resources- Use an abstraction that uses the system, not the system itself
    * File System
    * I/O
    * Networks
    * Clocks
* Low-level stuff shouldn't depend on high-level stuff- both should depend on abstractions
* Trying writing code without the dependencies first

## Types of Tests

### Parameterized Tests

* If there are a bunch of combinations of data with known results, lay them all out into a test

### Theory Tests

* Test all possible combinations
* Can be reduced with "assumptions"

### Generative Tests

* Computer picks the inputs
* Can be deterministic or not

### Pairwise Tests

* If there are too many possible combinations, make sure every category or pair of categories gets tested once

## Test Doubles

### Stubs

* Passing a fake object into a function to make it work
* Take control over indirect input this way
* Can be parameterized
* Stubs shouldn't have any conditional logic- don't replicate the objects you're stubbing
* Can also be used to allow a method to have side-effects

### Fakes

* Like a stub, but has interactive behavior which communicates back with the tested object
* Needs to be less complicated than the actual implementation

### Mocks

* Tests that side effects and indirect input occurred
* Assertion lives on the mock
* Still doesn't have business rules

### Spies

* A mock that reports its state rather than doing the assertion itself

### Dummies

* Fake data that you pass into a test that isn't important to the rest of the test

## TDD

1. Red - Failing test
1. Green - Passing test
1. Refactor - Good code
    * Never refactor while you're still red

Double-loop testing = Outside-in testing: Going from big tests to smaller ones

### What tests to write

1. The degenerate case- empty strings, 0, etc. Easiest to get to green with.
1. The happy path
1. Tests that uncover new knowledge
1. Error-handling and negative cases

### Strategies for Gettting Green

* Faking - Handing over exactly what's expected
* The most obvious implementation
* Triangulation - Letting each successive test guide the design

## Delete Tests That:

* Haven't kept up with refactoring
* Were "learning" tests that don't test anything meaningful
* Are commented out
* Don't compile
* Cover redundant things
* Are ignored
* Use an older testing framework
* You've "outgrown" as the design evolved

## Integration Tests

* Test databases with a transaction, then rollback
* Test services by spinning up a fake server in your test
* If your test spans a network, it must be failure-tolerant
* Your integration tests also test that API code returns the right format

## Acceptance Tests

* Need to handle async and variable delays
* Need to use real data (setup, run migrations + seeds)
* Abstract out concretions - "clickPaymentButton"
* Require true full-stack knowledge
* Require checks to see if environment is stable
* Get network dependencies on their own server
* Don't have every test add _and_ remove its own data
    * It's temporal coupling - defer to the environment
    * Always ensure the state at the beginning of the test
* You may want to build out some test data utilities
* You can assert lots of things in one run
