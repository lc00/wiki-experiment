## Vocab

* Iteratee - Invoked for every element, returns something
* Predicate - Returns true or false
* Comparator - Returns -1, 0, or 1

## Functions

### Searching

* `find` - Find a matching element
    * `findLast` - Get the last element returning true for predicate
    * `findIndex` - Get the index of the first matching element
    * `findLastIndex` - Get the index of the last matching element
    * `indexOf` - Get the index of a matching value
    * `lastIndexOf` - Get the last index of a matching value
* `sortedIndex` - Lowest index you can insert at and maintain sort order
    * `sortedIndexBy` - Accepts a function or string for property to look at
    * `sortedIndexOf` - `sortedIndex`, but the array should already be sorted
    * `sortedLastIndex` - Highest index
    * `sortedLastIndexBy`
    * `sortedLastIndexOf`
* `first` / `head` - Get the first element
    * `initial` - get all but the last element
* `last` - Get the last element
* `tail` - All but the first elment
* `nth` - Get the element at an index
* `take` - Get n elments from the beginning
    * `takeWhile` - Get elements from the beginning until condition is met
    * `takeRight` - Get elements from the end until condition is met
    * `takeRightWhile` - Get elements from the end until condition is met
* `findKey` - Get key of matching object
    * `findLastKey` - Get key of last matching object

### Transform Collection

* `map` - Transform each element in an array
    * `flatMap` - Maps a collection and flattens the result
    * `flatMapDeep` - Flattens deep
    * `flatMapDepth` - Flattens to specified depth
    * `invokeMap` - Calls a method for each item in a collection
* `reduce` - Accumulate a collection
    * `reduceRight` - Accumulate a collection starting at the end
* `groupBy` - Creates an object where the keys are groups returned by an iteratee
* `keyBy` - Create an object where the keys are determined by an iteratee
* `partition` - Split a collection into items that return truthy/falsy for a predicate

### Transform Array

* `flatten` - Flatten arrays 1 level deep
    * `flattenDeep` - Flatten arrays recursively
    * `flattenDepth` - Flatten arrays n levels deep
* `zip` - Group an array of values by object
    * `unzip` - Create an array of values by property
    * `unzipWith` - Create an array of values by property, specify how properties are combined
    * `zipWith` - Create an array of values by object, specify how properties are combined
    * `zipObject` - Create an object with keys
    * `zipObjectDeep` - Create an object with keys, supports using paths
* `concat` - Combine arrays
* `fill` - Fill all elements of the array with a value
* `fromPairs` - Make an object from key-value array pairs
* `reverse` - Reverse order (mutates)
* `join` - Turn into a separated string
* `chunk` - Splits an array into sized chunks

## Transform Object

* `toPairs` / `entries` - Make an array of key-value pairs from object
    * `toPairsIn` / `entriesIn` - Include inherited properties
* `mapKeys` - Change all the keys of an object
    * `mapValues` - Change all the values of an object
* `pick` - Get only matched properties from an object
    * `pickBy` - Get properties where the predicate returns true
* `omit` - Get everything but matched properties from an object
    * `omitBy` - Get everything but properties that match a predicate
* `transform` - Reduce, but for objects, iterates over properties
* `invert` - Swap keys and values
    * `invertBy` - Swap keys and values with a supplied transformation
* `castArray` - Converts to a collection

### Organize

* `shuffle` - Randomize the order of a collection
* `sortBy` - Sorts a collection by a property
* `orderBy` - Sort, specificying sort direction

### Filtering

* `filter` - Get an array of all elements returning truthy for predicate
    * `reject` - Remove all elements returning truthy for predicate
* `compact` - Removes all falsey values
* `pull` - Remove all elements matching value (mutates)
    * `pullAll` - Remove all elements matching values, like difference
    * `pullAllBy` - Remove all elements matching values, accepts function or string for key to compare
    * `pullAllWith` - Remove all elements matchings values, accepts a comparator
    * `pullAt` - Remove and return all elements at indexes
    * `remove` - Remove all elements matching predicate, like filter
* `without` - Remove all matching values
* `remove` - Remove values matching predicate
* `slice` - Get a subset of an array
* `uniq` - Get unique values
    * `uniqBy`
    * `uniqWith`
    * `sortedUniq` - Optimized for sorted arrays
    * `sortedUniqBy` - Optimized for sorted arrays
* `drop` - Drops elements from beginning
    * `dropWhile` - Drop until condition is met
    * `dropRight` - Drops elements from end
    * `dropRightWhile` - Drops elements from end until condition is met

### Set Operations

* `difference` - Get values from one array that aren't in others
    * `differenceBy` - Accepts a property or function returning the string to compare with
    * `differenceWith` - Accepts a comparator
* `intersection` - Get values that are in all arrays
    * `intersectionBy` - Accepts a property or function returning the string to compare with
    * `intersectionWith` - Accepts a comparator
* `union` - Get unique values from all arrays
    * `unionBy` - Accepts a property or function returning the string to compare with
    * `unionWith` - Accepts a comparator
* `xor` - Returns elements that aren't in all arrays
    * `xorBy` - Accepts a property or function returning the string to compare with
    * `xorWith` - Accepts a comparator

### Iteration

* `each` / `forEach` - Standard loop, early exit by returning false
    * `forIn` - Only own properties
    * `forOwn` - Only own properties
    * `eachRight` / `forEachRight` - Standard loop, backward
* `forOwn` - Objects, no inherited properties
    * `forOwnRight` - Objects, no inherited properties in reverse
* `forIn` - Objects, also inherited properties
    * `forInRight` - Objects, also inherited properties in reverse

### Predicates

* `every` - Returns true if all elements in the collection return true for predicate
* `includes` - Returns true if a collection contains a match
* `some` - Returns true if at least one of the elements is truthy for the predicate
* `eq`, `gt`, `lt`, `gte`, `lte`
* `isEmpty`

### Analyze

* `countBy` - Iterate through a collection and count the number of times a given property is returned
* `size` - Get the size of a collection
* `sample` - Get a random element
    * `sampleSize` - Get random elements

### Build Object

* `create` - Create an object with a particular prototype
* `assign` - Combine objects, clobbering from left to right. Mutates.
    * `assignIn` / `extend` - Also inherited properties
    * `assignWith` / `extendWith` - Customizes the assignment
    * `assignInWith` - Also inherited properties, customizes the assignment
* `defaults` - Doesn't clobber
    * `defaultsDeep` - Recursive
* `merge` - Also inherited properties, recursive, doesn't clobber if undefined
    * `mergeWith` - Also inherited properties, recursive, doesn't clobber if undefined, customizes the assignment
* `clone` - Shallow clone
    * `cloneWith` - Shallow clone with customizer
    * `cloneDeep` - Deep clone
    * `cloneDeepWith` - Deep clone with customizer

### Object Properties & Methods

* `at` - Get all properties at particular paths (eg. "someProperty.someOtherProperty[dynamicProperty]")
* `get` - Get a property at a particular path (eg. "someProperty.someOtherProperty[dynamicProperty]"), with default
* `result` - Get property at a particular path, invoking it if it's a function
* `has` - Check if an object has a path
    * `hasIn` - Check if an object or its prototypes have a path
* `set` - Set the value at a path
    * `setWith` - Set the value at a path, accepting a customizer for the path
* `update` - Set, but accepts a function to change the value
    * `updateWith` - Set, but accepts a function to change the value, accepting a customizer for the path
* `unset` - Remove a property, mutates
* `invoke` - Invoke the method at a path of an object
* `keys` - Get the keys of an object
    * `keysIn` - Get the keys of an object and its prototypes
* `values` - Get the values of an object
    * `valuesIn` - Get the values of an object and its prototypes
* `functions` - List functions declared on the object
    * `functionsIn` - List all functions, owned and inherited
