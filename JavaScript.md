## JavaScript

* Ecmascript is a language specification. A browser implementation (V8) is javascript.

## Types

* Primitives:
    * String
    * Number
    * Boolean
        * All values that are not falsy are truthy    
    * Null
        * Null is an empty value
    * Undefined
        * Undefined is the lack of a value at all
        * Undefined is not undeclared
    * Symbol (no collisions)
* Primitive: Not an object, no functions
* Primitives are always immutable
* Primitive wrapper (call a function on a primitive)

## Objects
    * `{}` - Object literals (didn’t use a constructor to make it)
    * Access with Dot notation (`Object.value`) vs. bracket notation (`Object[value]`)
    * JSON - JavaScript object represented as a string
    * Lodash <- Has object searching tools

## Object Constructors
    * Functions that you intend to be constructors start with a capital letter
    * Constructor functions don’t return anything
    * Using the new keyword give objects a prototype property

## Functions
    * Declarations get hoisted, function expressions don’t
    * Functions are objects, and can have properties and methods (static methods, constructors)
    * Functions are first-class
    * Functions that returns a function is called a “higher order” function (factories)
    * Inside a function, you have an `arguments` variable. `arguments` looks like an array, does not have array methods on it though.
    * Functions create scope
    * `()` is called the "invocation operator"

## Closures
    * A closure has access to it’s own scope, any outer functions scope (when it was defined), and any global variables.
    * `global` is `window` for Node.
    * Set `this` explicitly with `call()`, `apply()`, and `bind()`
        * `call` and `apply` <- first argument is `this`, the rest is arguments
        * `bind` <- returns a new function that is always bound to that context
        ```js
        return function myFunction(){
            this.somethingOrOther;
        }.bind(this);
        ```

## `this` Rules

1. Call, apply, bind
1. constructor with new (empty object with a prototype)
1. Method context User.myFunction() (this is User)
1. Global

## IIFEs

* Wrap function in `()` to make it an expression instead of a declaration
* Used to keep things out of the global namespace. Just for scope, encapsulation.
* Don’t need IIFEs in Node, since Node has modules

## Callbacks

* Used in async
* Callback is always last argument
* First argument to the callback should always be `error`
* Can name the function in callback

