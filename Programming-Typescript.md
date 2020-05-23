## Introduction

**Type Safety**: Using types to prevent programs from doing invalid things

## TypeScript: A 10_000 Foot View

**Typechecker**: A special program that verifies that your code is typesafe

Your code goes `TS -> TS AST -> Typechecker checks AST -> JS`

**Type system**: A set of rules that a typechecker uses to assign types to your program.

"You see this value here? Here's it's type!"

Each project should include:

`.tsconfig.json`

* Generate with `npx tsc --init`
```
// .tsconfig.json

{
  "compilerOptions": {
    "lib": ["es2015"], // What exists in the environment?
    "module": "commonjs", // What module system are you using?
    "outDir": "dist", // Where should your .js code go?
    "sourceMap": true,
    "strict": true, // Require all of your code to have types
    "target": "es2015" // Which JS version should your code compile to?
  },
  "include": [ // Where are your .ts files?
    "src"
  ]
}
```

`eslint.json`

* Generate with `npx eslint --init`

`index.ts`

## All About Types

**Type**: A set of values and the things you can do with them. Knowing a type lets you know valid values and valid operations.

Example: A Boolean is the set of all booleans (true and false), and the operations you can perform on them (||, &&, !)

* **Annotate**: Add the type to a value
* **Constrain**: Restrict a parameter to a value
* **Bounds**: Upper and lower values for something
* **Assignable**: An argument being compatible with a type
* **Type literal**: A type that represents a single value and nothing else. Good for maximizing type safety.
* **Structural typing**: A style of programming where you just care that an object has certain properties, and not what its name is (nominal typing). Also called "Duck Typing" in some languages.
* **Definite assignment**: Making sure that a value has been assigned before its used.
* **Index signature**: `[key: T]: U` - "All keys of type T must have values of type U."

### Types

`any`: Set of all values, which you can do anything with. Use a last resort. Top type.
`unknown`: Set of all values, but can only do comparison. If you check the type with `if (typeof thing === 'number')`, you can do type-specific operations. Will get Better than `any`.
`boolean`: Two values, you can compare them or negate them. You can annotate it as being a specific boolean (type literal), otherwise can always be inferred.
`number`: All numbers, `NaN`, and `Infinity`. All numeric operations. Also can always be inferred.
`bigint`: New, very large numbers.
`string`: Set of all strings, can concat, slice, etc. Also can always be inferred.
`symbol`: Can be annoted as unique. Rare. Just like a type literal.
`object`: Must specify the shape of the object. Can be inferred. Inferring doesn't do literal values since values are reassignable. Avoid emtpy objects, TS won't infer them correctly.
Arrays- `T[]` or `Array<T>`, eg `string[]`: Explicitly type. Typescript won't narrow your types if you create an array with an empty literal, it will just add each type to its inference. Keep arrays homogenous, or you have to type check them every time you want to do something with one of them.
Tuples- `[T...]`, eg. `[string, boolean]`: Mixed types. Have to declare up front or TS will assume its an array.
`null`: One value. Absence of value, eg. an error prevented something from being calculated. It's the subtype of all types except `never`, which means that every type is nullable, which means you always have to check if something exists first. `strictNullChecks` prevents this.
`undefined`: One value. Never assigned.
`void`: No explicit return value (eg. `console.log`)
`never`: No values. A function that never stops running, an exception throwing. The "bottom type," a proposition that's always false.

### Index signatures

Structure: `[key: keyType]: valueType`

```ts
let a {
  b: number
  c?: string // Optional
  readOnly d: number // `const` for properties
  readOnlyArray<string> // Optional syntax
  [key: number]: boolean // An unknown number of properties that have numbers for keys and booleans for values
  [someString: string]: string // A
}
```

### Type Aliases

You can use the `type` keyword to assign a type to a value. Makes your types more expressive. You can switch an alias for its type interchangeably. You can't declare a type twice. They're scoped and shadowed.

```ts
type Age = number
const kyle = {
  age: Age
}
```

### Unions and Intersections

Union is combined types, intersection is shared types. Unions are more common.

```ts
type Cat = { name: string, meows: boolean }
type Dog = { name: string, barks: boolean }
type CatOrDogOrBoth = Cat | Dog
type CatAndDog = Cat & Dog
```

A functions returned value might be something like `string | boolean`

### Enums

Fixed range of values. Don't use them in code that you publish, or it might conflict with someone else's. They are difficult to use safely, and can be avoided.

```ts
enum Language = {
  English = 100,
  Spanish = 200,
  Russian // Infers 301
}

Language.English
Language[200]
```

Or (safer):

```ts
const enum Language = {
  English,
  Spanish,
  Russian
}

Language.English
```

## Functions

* TypeScript generally can't infer parameters, but can often infer return type
* Parameters can be optional (must go last) or have defaults (don't need to be explicitly typed)
* `arguments` and `function` are unsafe

### Definitions

* **Formal Parameter** - Parameter
* **Actual Parameter** - Argument
* **Type Level Code** - Valid TypeScript, but not valid JavaScript on its own
* **Value Level Code** - Valid JavaScript
* **Contextual Typing** - Using a function signature type to get the types of parameters and return values
* **Overloaded function** - A function with multiple call signatures
* **Concrete Type** - A definite type, like boolean, Date[], { a: number } | { b: string }, (numbers: number[]) => number
* **Generic Type Parameter** - A placeholder type used to enforce a type-level constraint in multiple places. Also called a polymorphic type parameter.
* **Upper Bound** - A type that another type must have somewhere in its hierarchy

```
function add(a: number, b: number): number {
  return a + b
}

function add(...numbers: number[]) {
  return numbers.reduce((sum, number) => sum += number)
}

type someObject = {
  someKey: "someValue"
  someOptionalKey?: "someOtherValue"
}

function someFunction(): someObject {
  // Whatever
}

function typeThis(this: someObject): void {
}

// Typing a function signature
// When you do this, you don't need also annotate the parameters in the function definition ("contextual typing")
type Greeting = (message: string) => void

// Overloaded function signature
type Reserve = {
  (from: Date, to: Date, destination: string): Reservation
  (from: Date, destination: string): Reservation
}
// When you implement this, you need to combine it into one type:
let reserve: Reserve = (from: Date, toOrDestination: Date | String, destination?: string) => {
  // And then check to see which one it is:
  if (toOrDestination instanceof Date && destination !== undefined){
    // it's `to`
  }
}
```

### Generics

Generics are placeholders for type. You can indicate that multiple things need to be the same type, without specifying what they are ahead of time.

```ts
type Filter = {
  <T>(array: T[], fn: (item: T) => boolean): T[]
}
type Map = {
  <T, U>(array: T[], fn: (item: T) => U): U[]
}

type Whatever = <T = string>(T): boolean // default value
```

* Generics are like placeholder types
* `<T, U, V>` are the TS conventions, but they can be anything, including descriptive words
* Concrete types are bound at compile time, and are compiled differently for each instance
* Generic types generally inferred well, but may need to be explicitly bound as well (eg. Promises resolution values)

Generics can be scoped two different ways:

```ts
// Per signature
type Filter = {
  <T>(array: T[], fn: (item: T) => boolean): T[]
}
// or
type Filter = <T>(array: T[], fn: (item: T) => boolean): T[]
let filter: Filter = //

// For all signatures
type Filter<T> = {
  (array: T[], fn: (item: T) => boolean): T[]
}
// or
type Filter<T> = (array: T[], fn: (item: T) => boolean): T[]
let filter: Filter<number> = //
```

You can also use generics in type aliases, and pass those like parameters:

```ts
type SomeType<T> = {
  someKey: T
  someOtherKey: string
}

type SomeOtherType<T> = {
  someKey: SomeType<T>
  someOtherKey: boolean
}

type SomeConcreteType = SomeOtherType<string>
```

You can "bound" generics to at least be some concrete type (including joins and intersections), which preserves the original type while still bounding it.

```ts
type NodeMapper = <T extends TreeNode>(item: T[]): T
type NodeMapper = <T extends TreeNode & OtherNode>(item: T[]): T
```

## Classes and Interfaces

* Adds access modifiers, readonly
* Abstract classes can include overrideable methods
* Interfaces are lighter and just define a shape and can be extended, and can't include type expressions
* Interfaces can be declared multiple times and will merge
  * Interfaces can take in generics, but all generics must have the same type and name
* `this` can be a return type
* Classes are structurally typed- that means it doesn't check to see if the names are the same, only if the types are assignable
* Types and values have different namespaces, _except_ for classes and enums, which uses the same for both
* Classes generate types for both the Class itself as well as the constructor
* Classes can have generics, as can methods

```ts
class Piece<K, V> implements SomeInterface, SomeOtherInterface {
  constructor(
    private readonly color: Color,
    file: File,
    rank: Rank,
  ){
    this.position = new Position(file, rank)
  }
  something = (K): V => {
  }
}
```

### Mixins

* A mixin is just a function that takes in a class constructor and returns a class constructor

```ts
// Declares a new type that takes in a generic
// It is equal to a constructor that takes in any arguments, and returns that generic
type ClassConstructor<T> = new(...args: any[]) => T

//the function addDebug, which declares a generic, which gives a value for T
function addDebug
  <C extends ClassConstructor
    <{ getDebugValue(): object }>
  >
  // Takes in a class as an argument, it needs to be a class constructor
  (Class: C) {
    // Returns an anonymous class that extends the target class and has a debug method
    return class extends Class {
      debug(){
        let Name = Class.constructor.name
        let value = this.getDebugValue()
        return `${Name}(${JSON.stringify(value)})`
      }
    }
  }

const User = new addDebug(SomeClass)
const someUser = new User("a", 1, false)
someUser.debug()
```

### Decorators

Wrap a class and return a new one with new functionality. Not quite ready for primetime yet.

```ts
function serializable<
  T extends ClassConstructor<{
    getValue(): Payload
  }>
>(Constructor: T) {
  return class extends Constructor {
    serialize() {
      return this.getValue().toString()
    }
  }
}

@serializable
class APIPayload {
  getValue(): Payload {
    //
  }
}
```

## Advanced Types

## Handling Errors

## Asynchronus Programming, Concurrency, and Parallelism

## Frontend and Backend Frameworks

## Namespaces.Modules

## Interoperating With JavaScript

## Building and Running TypeScript

