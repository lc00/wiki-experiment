* Behavior: An operation with inputs, actions, and outcomes
* Feature: Desired product functionality, often involving multiple behaviors
    * What the customer expects to receive
    * It solves a problem

## Keywords

* Scenario: Specification of a behavior using formal steps and examples
* Given: The state the system should be in (not the actions the user took to get there)
* When: An action a user takes
* Then: An assertion about the new state of the system
* And: Follows a Given/When/Then (and matches the same type of step)
* But: Same as And
* Background: Shared givens and ands
* | Step tables |:
    * Used for structuring data
    * Passed into a step
    * First row is headers
    * Specific to that step
* """: Fence for long strings
* Scenario Outline:
    * Given a table of Examples
    * Examples tables provide input parameterization for the entire scenario
    * Each row should represent an equivalence class
    * Do you need to cover every combination?
    * Do columns actually represent seperate behaviors (are they always run together?)
    * Does the reader need all this data?
@tag: Groups tests

## Examples

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
```

## Good Gherkin

* The Golden Gherkin Rule: Treat other readers as you would want to be treated. Write Gherkin so that people who don’t know the feature will understand it.
* The Cardinal Rule of BDD: One Scenario, One Behavior!
* Write in third-person
* Givens should always use present or present perfect tense and active voice, and Whens and Thens should always use present tense and passive voice
* If the feature is just automating browser behavior, use `*` instead of one of the step keywords (it matches `Given()`)
* Given is active voice, When and Then are passive voice
* Describe what action should happen, not how to do it
* Third-person, first person doesn't give you a sense of what the person's motivations or privileges are
* Less than a dozen scenarios per feature
* Steps that use text blocks should end with "the text:"
* No step-by-step instructions
* Don't test data- a change in the underlying data shouldn't make the test fail
* Data isn't test data, it's examples of correct usage
* Hide data that doesn't need to be exposed to a non-technical user
* Scenarios should have a single-digit step count
* Separate scenarios by 2 blank lines
* Tags are lowercase hypen-separated
* Automation code can look hairy, but Gherkin should be elegant
* A feature documents the acceptance criteria for the feature, as well being requirements doc and descriptions
* As a/I want/So that is for features, Given/when/then is for acceptance critera
* Scenario titles should be:
    * Concise one-liners
    * Capitalize first letter
    * Describe what the behavior is, not why or how it's accomplished
    * No:
        * "and"
        * "or"
        * "but"
        * "because"
        * "since"
        * "so"
        * "should"
        * "verify"
        * "assert"
    * Use:
        * "receive"
        * "click"
        * "submit"
        * "search"
        * "select"


```gherkin
Feature: Google Searching

    Scenario: Search from the search bar
        Given a web browser is at the Google home page
        When the user enters "panda" into the search bar
        Then links related to "panda" are shown on the results page

    Scenario: Image search
        Given Google search results for "panda" are shown
        When the user clicks on the "Images" link at the top of the results page
        Then images related to "panda" are shown on the results page
```

```gherkin
Feature: Google Searching

    Scenario: Simple Google search
        Given a web browser is at the Google home page
        When the user enters "panda" into the search bar
        Then links related to "panda" are shown on the results page
```

```gherkin
# Examples cover multiple variants of the same behavior
Feature: SNES Mario Controls

    Scenario Outline: Mario jumps
        Given a level is started
        When the player pushes the "<letter>" button
        Then Mario jumps straight up

        Examples: Buttons
            | letter |
            | A      |
            | B      |
```

```gherkin
# Hides data in the automation- Specific links aren't mentioned
Feature: Google Searching

    Scenario: Search result linking
        Given Google search results for "panda" are shown
        When the user clicks the first result link
        Then the page for the chosen result link is displayed
```

```gherkin
When "Bob" logs in
```

```gherkin
Feature: Subscribers see different sets of stock images based on their subscription level

    Scenario: Free subscribers see only the free articles
        Given Free Frieda has a free subscription
        When Free Frieda logs in with her valid credentials
        Then she sees a Free article on the home page

    Scenario: Subscriber with a paid subscription can access both free and paid articles
        Given Paid Patty has a basic-level paid subscription
        When Paid Patty logs in with her valid credentials
        Then she sees a Free article and a Paid article on the home page
```

```gherkin
Given "test-user" navigates to page "landing-page"
When the user logs in
Then the page should display in logged in state
```

```gherkin
Scenario: The user logs in and sees the Home page
    Given the "Log In" page is displayed
    When the correct user credentials are entered
    And the "Login" button is pressed
    Then the "Home" page is displayed
    And the user details are displayed in the "Profile" section
```

```gherkin
# Improvement over specifying every form field- instead showing types of behaviors
Scenario Outline: Address entry
  Given the profile edit page is displayed
  When the user enters the "<address-type>" address
  And the user clicks the save button
  Then ...

  Examples: Addresses
    | address-type |
    | basic        |
    | two-line     |
    | foreign      |
```

## Bad Gherkin

```gherkin
# BAD EXAMPLE! Do not copy. Multiple When/Then pairs (actions), describes actions in the Given
Feature: Google Searching

    Scenario: Google Image search shows pictures
        Given the user opens a web browser
        And the user navigates to "https://www.google.com/"
        When the user enters "panda" into the search bar
        Then links related to "panda" are shown on the results page
        When the user clicks on the "Images" link at the top of the results page
        Then images related to "panda" are shown on the results page
```

```gherkin
# BAD EXAMPLE! Do not copy. Language is not subject-predicate.
Feature: Google Searching

    Scenario: Google search result page elements
        Given the user navigates to the Google home page
        When the user entered "panda" at the search bar
        Then the results page shows links related to "panda"
        And image links for "panda"
        And video links for "panda"
```

```gherkin
# BAD EXAMPLE! Do not copy. Tenses are incorrect.
Feature: Google Searching

    Scenario: Simple Google search
        Given the user navigates to the Google home page
        When the user entered "panda" at the search bar
        Then links related to "panda" will be shown on the results page
```

```gherkin
# BAD EXAMPLE! Do not copy. There is no "Or".
Feature: SNES Mario Controls

Scenario: Mario jumps
    Given a level is started
    When the player pushes the "A" button
    Or the player pushes the "B" button
    Then Mario jumps straight up
```

```gherkin
# First person, procedural
Given I visit "/login"
When I enter "Bob" in the "user name" field
And I enter "tester" in the "password" field
And I press the "login" button
Then I should see the "welcome" page
```

```gherkin
# First person, procedural
Feature: Subscribers see different sets of stock images based on their subscription level 

Scenario: Free subscribers see only the free articles
    Given users with a free subscription can access "FreeArticle1" but not "PaidArticle1" 
    When I type "freeFrieda@example.com" in the email field
    And I type "validPassword123" in the password field
    And I press the "Submit" button
    Then I see "FreeArticle1" on the home page
    And I do not see "PaidArticle1" on the home page

Scenario: Subscriber with a paid subscription can access "FreeArticle1" and "PaidArticle1"
    Given I am on the login page
    When I type "paidPattya@example.com" in the email field
    And I type "validPassword123" in the password field
    And I press the "Submit" button
    Then I see "FreeArticle1" and "PaidArticle1" on the home page  
```

```gherkin
# Too specific, too technical
Given the user navigates to "http://training-page.testautomation.info/"
When the user fills in "test" for "#login-username"
And the user fills in "test" for "#login-password"
And the user clicks on button "submit"
Then the page should display in logged in state
```
