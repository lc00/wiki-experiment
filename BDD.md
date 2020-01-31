## BDD

Superior to TDD because it marks actual progress in the development of the system. TDD tests components, BDD tests features.

### Tips

* Remove duplication in your test descriptions by nesting `describe` and `context`.
* `before` is safe with immutable/stateless code. Otherwise, use `beforeEach`.
* `describe` is for features, `context` is for different setups for that feature (scenarios).
* Find the entities, then figure out which actions the entities can take. Each action needs a feature. Display information is a feature too. Each feature has a different setup or input data which should result in a different output- these are scenarios, and each needs a separate test.
* Extract fixture creation to factories
* Name your test files `role`-`action`-`entity`, eg. "customer-displays-order"
* Features are present tense, test titles are future tense, eg. "It will show no order items"

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

* Behavior: Operation with inputs, actions, and expected outcomes
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

### Discovering Scenarios

Would the outcome of the user operation be different if:

* The system is in a different state
* If some of the systems you need to interact with
    * Don't respond quickly or return an error
    * Return different valid responses
* If the user
    * Performs a different action before the current one
    * Has different credentials
    * Enters incorrect information

For each each feature, there should only be one action that is the same across scenarios.

### Discovering Tests Within a Scenario

* What's the new state of the system
* What's the response of the system to the user
* Which set of actions are available to the user in the new state
* What possible interactions are there with other systems
* Other side-effects

### Sinon

* `.callsArgWithAsync(indexOfCallbackFunction, argument1ToSendToCallback, argument2ToSendToCallback)`
* `chai-as-promised` adds `.eventually` to test for promises

## Example Mapping

[Original Article](https://cucumber.io/blog/bdd/example-mapping-introduction/)

* Should take about 25 minutes per user story

### Process

* A story is on a yellow card at the top of the table
* Rules are under it on blue cards
* Examples of rules are on green cards under the rules (use "The one where...")
    * "The one where the customer forgot a receipt"
    * "The one where the product is damaged"
    * "The one where the product was bought 15 days ago"
* Questions are in red cards on the side

### Problems

* A table full of red cards means you don't understand it well enough yet
* A table full of blue cards means the feature is complicated and should be split
* A table full of green cards means the rules are compound and should be teased apart
