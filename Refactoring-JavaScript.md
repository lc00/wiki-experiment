## Refactoring

* Refactoring changes code while ensuring behavior stays the same. Otherwise, you’re just changing code. The interfaces need to stay the same.
* Make the data independent from the program.
* CPS = “continual passing style”, keeps passing values through, no outside state

### Rename variables to remove

* Mispelling
* Short names and abbreviations
* Non-descriptive and general names
* Numbers in names
* Names that are used more than once
* Not CapitalCase for constructors
* Not camelCase for variables and methods
 
### Remove useless code

* Dead code
* Speculative code
* Comments - put tasks and to-dos elsewhere, keep doc-generating comments
* Whitespace, `EOL`, `EOF`
* Do-nothing code
* Logs and debugs

### Variable Refactoring

* Remove magic numbers and strings
* Break up long lines, use shorthand operators
* Inline short function calls
* Cache lookups
* Don’t hoist variable declarations, do hoist functions
* Remove variables with duplicate information
* Fix `self = this` statements
* Use `_` for privacy, not a complicated pattern

### String Refactoring

* Use template strings over concatenation
* Remove magic strings
* Use regex to search strings

### Array Refactoring

* Break up long lines on commas, or group them together
* Use `map` instead of pushing into new arrays
* `for of` loops are better than `for` loops for arrays/objects
* `forEach` is preferable to for loops

#### Array/Object Alternatives:

* Use `Set` for all unique values
* Use objects instead of arrays for named keys
* Use `Map` for:
    * Not hierarchy/prototypes
    * Elements are all similar
* Use `WeakSet` and `WeakMap` for
    * No sizing
    * No iteration
* Use a bit field as an alternative to an array of booleans

### OOP Refactoring

* Subclass to avoid conditionals
* Unnecessarily nested hierarchy is hyperextension, fix it by pushing things higher up the hierarchy until the tests still pass

### FP

* Reduce arity (number of parameters) with partial application

### Extracting and inlining functions

* Should be a natural, fluid process
* Get away from “running the file” imperatively
* Wrap sequential statements in functions
* Inline if the function doesn’t really do anything
* Inlining variables makes extracting functions easier
* Take things out of the global namespace and put them in an object
* Extracting named functions may reduce the clarity of your code

## Quality

Testing leads to confidence, confidence enables refactoring, refactoring leads to quality.

### Quality Tools:

* SOLID
* DRY
* KISS
* GRASP (General Responsibility Assignment Software Pattern)
* YAGNI
* EVAN
    * Extract functions and modules to simplify interfaces
    * Verify code behavior through tests
    * Avoid impure functions when possible
    * Name variables and functions well
* Style guides
* Developer happiness meetings
* Pairing
* Code Review
* TDD / BDD
* Test frameworks
* Assertion library
* Domain-specific drivers
* Factories & fixtures
* Mock/stub libraries
* Build/Task/Packaging tools
* Loaders/Watchers
* Test Run Parallelizer
* CI Server
* Coverage Reporters
* Linters
* Logger/Debugger
* Staging/QA Servers

Quality might mean code/test coverage, low complexity, number of arguments to functions, low length of file. Tech debt is complexity and lack of coverage.

### Parts of a function

* Function bulk comes from lines of code and cyclomatic complexity (different paths through code, caused by conditionals)
* Inputs. Can be explicit, implicit (`this`), non-local. Preference in that order. Bind or pass this.
* Outputs. Don’t return `null` or `undefined`, don’t return different types out of the same function.
* Side-effects. Minimize them.

### Sources of variation

* `Math.random`
* `new Date`
* Calls to external URLs

## JavaScript

* `use strict` speeds up JavaScript, but takes features out.
* Which “JavaScript”? JS Implementation -> Platform -> Framework -> Library
* You can use named parameters in options objects with destructuring.
* `Maps` use `get`/`set`, can be converted to arrays, and are the same as hashes/dictionaries in other languages
* Your first function in a promise chain must be thennable, but you can cheat with `Promise.resolve().then()`

## Testing

* * A mock asserts; a stub does not.
* TDD is more like making soup than baking.
* `it` doesn’t need to be in a `describe` or assert anything.
* You can write your tests directly inside of the file being tested.
* Write tests for anything you need confidence in
* Factor out randomness by putting conditionals and ranges in the test
* `tape` is super easy JS testing
* You can add functions to objects in tests, and then call them during the assertion
* You can call an async function in a test and just work with the result

### Why testing

* You’re already doing it
* It’s a necessary part of refactoring
* Makes working with a team easier
* Demonstrates functionality
* Verify behavior of 3rd party code
* Necessary for big upgrades
* Catches bugs earlier
* Smoothes out the dev cycle by eliminating tech debt
* Creates a tight feedback loop

### Types of tests:

* Manual
* Documented-manual (the “QA Plan”)
* Approval test (a human verifies the output, and their choice is saved)
* Unit test
* Non-functional test
* Performance
* Usability
* Play testing
* Security
* Accessibility
* Localization
* Feature test (for test-first)
* Regression test (reproduces bug)
* Characterization test (a feature test after the fact- if no side-effects, passing means done)
* Mutation testing (programmatically changes inputs to functions)

## OOP

* Extract shared state & behavior to classes
* Only use default arguments if they are true defaults, not just common cases
* You can build hierarchies with:
    * Classes (preferred)
    * Object literals
    * Factory functions
    * Constructor functions
* You can make mixins with `Object.Assign` (objects on right clobber objects on left)

### OOP Patterns

#### Template Method

Helps get rid of conditionals.

```js
class SuperClass {
  log(n){
    this.specificMethod(n);
  }
}
class aSubClass(){
  specificMethod(n){}
}
class theSubClass(){
  specificMethod(n){}
}
```

#### Strategy

* Pass function definition in constructor
* Can package all strategies together in an object

#### State

* Combinations of state & behavior bundled together

#### Null Object

* Make an object that handles null and returns this, “”, false, etc.
* Generally mirrors the full API
* Alternative to null checks

#### Decorator

* Add trait to something you don’t own- doesn’t modify original class.
* Can be used to convert null to null objects
* Use factory functions instead of constructors (has a return value, would never be instantiated)

```js
function NewTrait(oldObject){
  const newObject = Object.create(oldObject);
  newObject.newTrait = "hey";
  return newObject;
}
```

#### Adapter

* Converts 2 dissimilar interfaces.
* Maps interfaces together, but otherwise similar to decorator
* Decorator and adapter are both more complicated than changing underlying code

```js
    constructor(adapter){
      this.newMethod = adapter.oldMethod;
    }
```

#### Facade

* Simplify an interface or create a DSL
* jQuery is a DOM facade

#### Memo

Cache results of expensive calculation in a lookup table

## Functional Programming

* Time and order makes something imperative
* Spreadsheet functions are a good example of declarative programming

### Restrictions:

* No variables
* No global state
* Functions must return
* Every if must have an else (otherwise would mutate state, side effect, throw)
* Function declarations have typed signatures
* Type-safety during compilation
* No null
* Side effects are difficult
* Functional purity
* Idempotence (same input gives you the same output)
* No side effects

### Benefits:

* No race conditions (easy concurrency and scaling)
* Type safety == confidence
* No null checks
* The evaluation of an expression is the same as the value it produces (“referential transparency”)
* Works well with many cores and lots of memory

### Basics

* Don’t do assignment (or reassignment) in conditionals or loops
* Don’t do destructive functions or mutate
    * `functionName!` For destruction, `functionName?` For boolean
* Minimize state/scope with IIFEs
* Get rid of conditionals w/
    * Polymorphic subclasses
    * Delegation of properties
    * Extracting to separate functions

### Advanced Basics

* Partial application - return a function (first argument applied)
    * Compose functions out of other functions
* Currying - chain calls
    * Ramda gives you a utility for it
* Save specific kinds of maps
* Point-free (no named parameters)
* You can memoize any function with Ramda because the results are idempotent

#### Hindley-Milner Type System

`functionName :: InputType -> InputType -> OutputType`  
`(functionInput -> functionOutput)`  
`[arrayValue]`

Can curry inputs to make new functions

## Workflow

* Too much frustration and excitement means that your feedback loop is too long.
* Make programming boring.
* Write badly to get to green, copy/paste code, but use tools to catch bad stuff, then refactor.
* Commit after every green.

Refactoring legacy code:

* Put JavaScript in it’s own file
* Put the project under version control
* Pick a testing strategy
