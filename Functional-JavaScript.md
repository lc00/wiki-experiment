## FP vs. OOP

* OOP breaks problems into nouns, FP breaks problems into verbs
* OOP is about subtly modifying the state of objects, while FP is about minimizing observation state changes- minimizing the surface area of change to the smallest area possible
* Functions are used to abstract out behavior
* FP uses first-class functions (functions stored and used as values)

## Speed

Functional code is slower than imperative code, all things being equal. All things aren't equal, though. Static optimization can "inline" (copy/paste) the imperative code from a functional implementation.

## Predicates to Comparators

* A predicate returns `true` or `false`
* A comparator returns `-1`, `0`, or `1`
* You can use a function to translate a predicate to a comparator

```
function toComparator(predicate){
    return (x, y) => predicate(x, y) ? 1 : -1;
}

function isGreater(x, y){
    return x > y;
}

[3, 2, 1].sort(toComparator(isGreater))
```

## Applicatives

"Apply" a function to table-like data

* `map`, `filter`, `reduce`
* `all`, `any`
* `find`, `findWhere`, `where` - Find matches
* `reduceRight` - Reduce, but starts at the end of the collection
* `reject` - Opposite of `filter`
* `sortBy` - Sorts a collection of objects based on a property
* `groupBy` - Array to object, keys are the group, values are an array of matches
* `countBy`
* `pairs` / `object` - Split an object into an array of key/value arrays, or combine them back into an object
* `invert` - Flips an array (such as to reverse keys and values)
* `omit` / `pick` - Removes a key from an object, like a password / Whitelist keys for an object
* `keys`, `values`, `pluck` - Get the keys, values, or all the values for one key in an array of objects
* "Collection-centric programming"

## Scope

* Lexical scope - Look up the scope from inner to outer
* Dynamic scope - Defined at run-time (`this`), uses a stack
* Function scope vs. Block scope
* Free variable - Closed-over variable referenced in an inner-scope
* Shadowing - Overwriting a variable in an inner scope

## Higher-Order Functions

Given a collection of people, finds the oldest person:

```js
finder(plucker("age"), Math.max, people);
```

* For: Use functions for iterating somemthing a specific number of times (`repeatedly`)
* While: `function iterateUntil(fn, test, initialValue)`
* Static values are often represented with `k`
* Combinator: Lambda with no free variables
* Currying: Returning a function from a function
* Use a free variable to have shared state between multiple calls to the same function (incrementor)- this isn't pure and makes a function stateful though
* Referential transparency: Only reliant on input to produce output, no free variables
* Return a function with a bound parameter is a way to "configure" an object
* You can attach metadata to a function as a property, like an error message, and return it in a higher-order function

## Functional Composition

Snapping together functions like legos.

* Dispatching: Try each of these functions in order until one of them returns a value
* You can use a chain of functions to replace a switch statement. Each function takes a test function and a function that will be invoked if the test passes. If the function returns undefined, it tries the next function.
* Mutation is a low-level operation - hide it as far down as you can.

```js
const someDataTransformation = dispatch(
    isA("notify", notifyUser),
    isA("join", joinUser),
    alertUser, // default
);
```

### Currying

Create a function that returns other functions, applying the arguments from the first

* Used to create fluent interfaces and build new functions
* Can be done from the right or left
* `curry1`, `curry2`, `curry3` - If the number of parameters is arbitrary, use partial application instead

```js
function outside(variable1){
    return function inside(variable2){
        return variable1 * variable2;
    };
}
```

### Partial Application

Currying builds a function that has access to free variables, partial application progressively binds arguments to functions

```js
function outside(variable1){
    return inside.bind(null, variable1);
}
```

```js
function square(number){
    return number * number;
}

// `condition` accepts validators, and returns errors if validations fail or applies the bound function otherwise
const squarePostConditions = condition(
    validator("Needs to be greater than 0", greaterThan(0)),
);
const squarePreconditions = condition(
    validator("Must a number", isNumber),
);

// `partial` calls the first function, and binds the second function as its first argument
const validatedResult = partial(squarePostConditions, identity);
const validatedSquare = partial(squarePreconditions, square);

// Evaluates right to left
const safeSquare = compose(
    validatedResult,
    validatedSquare,
);

safeSquare(2);
```

This code:

* Passes 2 to the `safeSquare` function
* The 2 is passed into the `validatedSquare` function
* `validatedSquare` applies the preconditions to 2
    * If there are no errors, it passes 2 to the square function, which was bound as its first argument
* 4 is passed to the `validatedResult` function
* `validatedResult` passes 4 to the `squarePostConditions` function
    * If there are no errors, it passes 4 to the identity function, which was bound as its first argument

## Recursion

Reasons to use recursion:

* One abstraction that's applied to progressively smaller subsets
* Recursion can hide mutable state
* Can process lazily and work with infinitely large lists

How to write a self-recursive function:

1. Know when to stop
2. Decide how to take one step
3. Break the problem into that step and a smaller problem

* Can be used to walk a graph. Can keep memory of visited nodes, passing those in to each call as well
* A tail-recursive call is one that makes the recursive call as its last step. Some languages use this to clean up resources used by intermediate steps- otherwise you'll blow the call stack with large data.
* Conjoin and disjoin: Using recursion to make `and` and `or` with short-circuits
* Can be used to deep clone
* Codependent functions (mutually recursive) are functions that call each other
* Can be used to flatten arrays

Trampolining is where nested calls are flattened out, thus getting around call-stack limitations. Each call returns a partially applied function. Instead of calling it once, the trampoline calls every successive function until they're done. This transfers the problem from the call stack to the heap, which is much larger.

To work with infinite data, split the data into the head and the tail.
