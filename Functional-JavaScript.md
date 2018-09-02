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
