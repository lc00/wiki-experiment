* Putting `async` in front of a function declaration make it an `AsyncFunction` object and is treated like a promise
* `await` can only be used inside of `AsyncFunction`s
    * Ergo, can't be used at the top level
* `await` pauses the execution of the function until the promise that you pass it resolves, kind of like a generator

```js
async function somethingThatUsesAwait(){
    const result = await networkRequest();

    return result;
}

somethingThatUsesAwait().then(result => {
    // Using promises now
});
```
