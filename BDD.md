## BDD

Superior to TDD because it marks actual progress in the development of the system. TDD tests components, BDD tests features.

### Tips

* Remove duplication in your test descriptions by nesting `describe` and `context`.
* `before` is safe with immutable/stateless code. Otherwise, use `beforeEach`.
* `describe` is for features, `context` is for different setups for that feature (scenarios).
* Find the entities, then figure out which actions the entities can take. Each action needs a feature. Display information is a feature too. Each feature has a different setup or input data which should result in a different output- these are scenarios, and each needs a separate test.
* Extract fixture creation to factories

```js
describe("A feature", () => {
    context("for a given setup of inputs", () => {
        beforeEach(() => {
            // Setup code
        })

        it("like this specific one, it does this", () => {})
        it("like this other one, it does this", () => {})
    })
})
```

### Terms

* Feature: Single concrete action that a user can perform on the system. This will change the state of the system and/or make the system perform actions on third-party systems.
* Test Double: Objects that impersonate real third-party systems or components. It is common for a double to be both a spy and a stub.
    * Fakes: Some logic
    * Stubs: Hard-code values (assertion)
    * Spies: Record interaction (set up)
    * Mocks: Self-validating spies
* Triangulation: Writing more tests with different inputs to try to expose duplication in your code. Each one will make your code uglier until the pattern emerges. Each different input is called an "example." Examples should:
    * Be meaningful from the point of view of the problem domain
    * Break the current implementation
    * Cover edge cases
* Parameterized test: Wrapping the `it` in a function that gets called with multiple inputs
* Scenario: Different execution path for the same feature
