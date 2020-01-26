## Setup

`npm i -D cypress-cucumber-preprocessor`

### `package.json`

```
    "scripts": {
        "test": "npx cypress open",
        "ci": "npx cypress run --spec **/*.features"
    },
    "cypress-cucumber-preprocessor": {
        "nonGlobalStepDefinitions": true,
        "cucumberJson": {
            "generate": true,
            "outputFolder": "cypress/cucumber-json",
            "filePrefix": "",
            "fileSuffix": ".cucumber"
        }
    },
```

### `cypress.json`

```
{
    "baseUrl": "http://localhost:8080",
    "chromeWebSecurity": false,
    "testFiles": "**/*.{feature,features}"
}
```

### `cypress/plugins/index.js`

```
const cucumber = require('cypress-cucumber-preprocessor').default
module.exports = on => on("file:preprocessor", cucumber())
```

### `cypress/support/commands.js`

```
Cypress.Commands.add("the", testSelector => cy.get(`[data-test-${testSelector}]`))
Cypress.Commands.add("theFirst", testSelector => cy.get(`[data-test-${testSelector}]`).eq(0))
```

### `cypress/integration/_all.features`

(Just include this file blank to help with CI not launching new browser instances for each file)

## Creating Tests

A test file is structured like this:

```
cypress
    |- integration
        |- common
            |- some-shared-step.js
            |- more-shared-steps.js
        |- SomeFeature.feature
        |- SomeFeature
            |- any-file.js
            |- any-other-file.js
```

## Writing Tests

### Features

* Feature: A small, concrete action that the user can perform on the system; this will change the state of the system and/or make the system perform actions on other systems
* Scenario: Different execution path for the same feature

```gherkin
Feature: The description of the feature goes here

    As a user, I want feature, so I can get benefit.
    You can also link to documentation here, etc.

    Background:
        Given I open the page # This runs once before each scenario

    @some-tag @another-tag # ` npx cypress-tags run -e TAGS='not @some-tag and (@not-tag or @another-tag)'`
    Scenario: Opening the page
        Given another thing
        When you do nothing
        And you do nothing
        But you don't do anything
        Then the page displays "Main heading" # "Main heading" is passed as an argument

    @focus # Only runs this scenario
    Scenario: Some parameters
        When you give a "word" and a bunch of data:
            | firstKey  | secondKey |
            | A         | B         |
            | 1         | 2         |
        Then the page displays "AB12"

    Scenario Outline: Use juicer with <fruit>
        Given I put "<fruit>" in a juicer
        When I switch it on
        Then I should get "<juice>"

        Examples:
        | fruit      | juice            |
        | apple      | apple juice      |
        | pineapple  | pineapple juice  |
        | strawberry | strawberry juice |

### Specs

```js
const {
    Given
    When,
    Then,
} = require("cypress-cucumber-preprocessor/steps");
const { server, route, log, visit, the, theFirst } = cy

beforeEach(() => { // Only use this for purely technical abstraction
    server()
    route(/* something */)
})

Given("I open the page", () => {
    visit("/")
})

When("you give a {string} and a bunch of data:", (word, table) => {
    // word is a passed argument
    // table gives you access to things like table.hashes()
})

Then("the page displays {string}", word => {
    expect(word).to.equal(word)
})

Then("the page displays {string}", title => {
    theFirst("main-heading").should("have.text", title)
})
```