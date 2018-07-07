## The Testing Pyramid

* UI tests are powerful, but slow and brittle, and speed matters
* Levels of testing apply to levels of architecture:
    * UI - UI. Use sparingly.
    * Integration - Service. Cover unit test gaps.
    * Unit Tests - Logic. Favor over UI tests.
* Unit tests are what enable you to iterate quickly

## Smoking User Interface Tests

* Smoke test- Are our applications correctly deployed, environments correctly configured, and pieces of our architecture hooked up correctly?
* Use variables for commonly used URLs
* Record/playback UI tests are brittle and unreadable
* UI tests are more likely to be unreliable, and don't give very specific feedback about why something broke

## Adding UI Tests to Legacy Systems

Steps: 

1. Confirm you're on the right page
2. Find the right selectors (prefer IDs)
3. Make assertions

* The tighter you couple the test to your interface details, the more brittle it is.
* Use `before` blocks for clean up and setup

## Connecting the Dots with Integration Tests

* Testing web services

## Integration Testing RESTful Web Services

* Isolate your test cases

### GET

* Add relevant data to your database in the test

### POST & PUT/PATCH

1. Look for something
2. Verify that it isn't there
3. Create it
4. Search for it again
5. Assert that it is there

You can also assert the length of the response, add 1, and assert the length has increased, but you lose the detail.

### DELETE

1. Look for something
2. Verify it's there
3. Delete it
4. Search for it again
5. Assert that it isn't there

## Covering Our Bases with Unit Tests

* Testing is about confidence. Test that things work, and test the things that could possibly break.
* Never connect to the network in a unit test

Things to look for:

* Happy paths- What should it do?
* Special cases- Boundary conditions
* Exceptions- Under what conditions might it break?
* Program logic and flow- Do all of the conditionals work?

### Dependency Injection & Mocking

* Pass your dependencies into constructors
* Use mocks to make sure a collaborating method or object was called a certain way

## Unit Testing in the Browser with JavaScript

* You can also test the UI without going end-to-end
* Build out HTML fixtures in your tests and run your code against them
    * Can also import them
    * Run the risk of getting out of sync with production HTML
* Use spies on functions to prevent network requests

## Climbing the Pyramid

* Unit tests: everything that could possibly break
* Integration tests: check the plumbing, don't sweat the details
* UI tests: your insurance

Fixing flaky tests:

1. Rewrite the test to leave out flakier details
2. Push the test further down the pyramid
3. Delete it- it's not worth it

## Programming 101

* Refactor duplicated code in tests to before functions

## Organizing Tests

* Your setup code shouldn't have setup that applies to some tests and not others. Group data as close to where it's going to be used as possible.
* Test one _thing_ per test, but not necessarily one assertion
* Group like things together, use nested `describe`s to give them clear names (ideally as short as possible). This is called "embedding the context."
    * Your nested `describe`s should read like one sentence

## Effective Mocking

* For controlling and monitoring objects that are deep in the tests, and testing without calling the real service
* Mock/Test-Double - Can be remote-controlled and monitored
* Stubs - Return hard-coded data
* Prefer injecting mocks into the code's constructor/arguments
* Every mock represents some degree of coupling
* Don't test private APIs
* "Swamp of mocking":
    * More mock, expectation, and setup code than test code
    * You don't want to change production code because too many tests would break
    * You don't remember what the original intent of the test was
* Instead of mocking (eg. sinon), capture the output of the real thing (eg. nock). This is also coupling, but more stable coupling.

## Writing Tests First

* Red - Focus on overall API design for code that doesn't exist
* Green - Anything to make it pass
* Refactor - With tests at your back, make the design good

TDD with UIs is hard, because the interface changes rapidly early on.
