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

## Classes and Interfaces

## Advanced Types

## Handling Errors

## Asynchronus Programming, Concurrency, and Parallelism

## Frontend and Backend Frameworks

## Namespaces.Modules

## Interoperating With JavaScript

## Building and Running TypeScript

