## Types

* Built-ins - `number`, `boolean`, `undefined`, `string`, `object` (non-primative)
    * `null` and `undefined` are legal values for any other type (disablable)
* New types:
    * `:any` - Disables type checking
    * `void`
    * Arrays: can be done as `number[]` or `Array<number>`
    * Tuples: `let x = [string, number, string]`
    * Enum: `enum Color {Red, Green, Blue}`
        * Keeps numeric values
        * `let color: Color = Color.Green; // 1`
    * `never`: Errors, things that should never be called
    * `ReadonlyArray<TypeGoesHere>`: No mutation methods

## Interfaces

Don't need to declare the object has having implemented the interface.

```ts
interface Person {
    name: string;
    optional?: boolean; // Optional property
    readonly dontWriteMe: string; // Like const for properties
    [propName: string]: any; // Any other properties
}

function announcePerson(person: Person) {
}
```

```ts
interface SendMessage {
    (recipient: Person, message: string): void
}
let messageFunction: SendMessage

messageFunction = function(recipient: Person, message: string): void {
    //
};
```

## Destructuring

Comes after

```ts
const { old: new } : { old: number} = { old: 1 }
```

## Type Assertions

Make a type (like `any`) more specific.

```ts
let aString: any = "hey";
let aStringLength = (aString as string)
```

or

```ts
let aString: any = "hey";
let aStringLength = (<string>aString).length;
```

## Compiling

`tsc`

* `--strictNullChecks` - Saves a lot of headaches
