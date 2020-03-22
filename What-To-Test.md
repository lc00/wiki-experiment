Changing an implementation shouldn't break a test.

## Units

* Public methods
* All branches of code execution
* Unexpected user inputs
* Stub behaviors of other units
* Shallow mount

### Not

* Interactions between units
* Library behavior
* Boilerplate

## Integration

* Integration between units that have been stubbed
* Integration between applications you control
* Edge and failure cases between units
* Interactions that don't cross boundaries

## Components

* Favor pure components
* No implementation details
* Full mount

## Features

* Common user interactions
* Common error cases
* UI logic that isn't covered by units
* Calls to third-party services

### Not

* Edge cases
* Parts that have no user behavior
* Third-party services
