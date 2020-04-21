## Focusing On Value

BDD is:

* Exploring desired system behavior with examples in conversations
* Formalizing examples into automated tests to guide development

Most BDD stuff focuses on the latter, but the former is more difficult. BDD uses examples rather than abstract specs.

Most teams lay sprints and Scrum rituals over the work as they've always done it. They commit to big projects, detail the scope in a requirements document, convert those requirements into a backlog, and don't deliver potentially shippable product increments. Testers and product people are bored early on, and overwhelmed later on.

### MMFs and Stories

A minimal marketable feature (MMF) is the smallest set of functionality that's worth shipping to users. These are split into user stories, which are small slices of system behavior that provide increments of value to users and some visibility into progress for you. MMFs are analogous to "Minimum effective dose" in medicine. Too much of a feature has negative side effects too: delays, missed market windows, opportunity cost, waste, etc.

Example MMF: "Find Kindle books by title and borrow them"

A user story is a description of a change in system behavior from the perspective of a user. They measure progress toward an MMF.

If the primary user is described in a product vision (who), you can use the story title to describe only the what/why with the "in order to ----, I want to ----" format.

Stories should earn their ways into MMFs. You don't want nice-to-have stories holding essential stories hostage.

Don't worry about prioritizing stories within an MMF- it all has to be released at once, by definition. Focus on the stories where you can learn a lot or mitigate a lot of risk.

Example Stories for this MMF:

* In order to find the specific ebook I'm looking for, as a library patron, I want to search the ebook catalog by title.
* In order to actually read the book, I want to be able to check out an ebook to my Kindle
* In order to get more ebooks I want in the library, I want to be able to tell a librarian when searching by title that I didn't find the book I wanted

### Feature Mining

To get an MMF, use feature mining:

* Get enough people together to represent the technical and business perspectives
* Answer these 4 questions:
  1. What's the value or impact? Why is this worth doing? What benefits go to whom? What's the value that makes all ofo the other things we could relatively unimportant?
  2. What makes it big? Why does it need to be sliced at all? What is there many or much of? What always takes a long time, even if it's well-understood? What contributes disproportionately to the size of the effort?
  3. What are the risks? What irreversible negative consequences could happen? Example: "We're not able to optimize the performance enough for the reports to run overnight" Which risk is scariest or most likely to derail the project?
  4. What are the uncertainties? What important questions do we need to answer for this to succeed? What uncertainty is most critical to resolve?
* If a question has more than one or two answers, narrow them down to the most important answers
* Brainstorm possible ways to slice the big idea that get you a good piece of value, mitigate some risk, and give you some learning without the things that make it big.
  * "How can we get some of this top impact/mitigate this risk/answer this question without taking on the bigness?

### Story Splitting Patterns

* **An MMF is big because it has multiple steps**. Look for a story that takes a thin slice through the whole workflow, and write stories for the rest of it.
  * Checking out one hard-coded book
  * Finding and borrowing only one book at a time
* **An MMF is big because it includes multiple operations**. Use one story for each operation.
  * Creating an account
  * Viewing account details
  * Changing a password
  * Changing account details
  * Canceling account
* **An MMF is big because it includes many business rule variations**. One story per rule.
  * Late fees for adults
  * Late fees for children
* **An MMF is big because of the variety of data**.
  * System works in English
  * System works in Spanish
* **An MMF is big because the interface is complex.** Start with a simple interface and add the complexity.

## Exploring With Examples

### Games

In competitive games, there is winning/losing, in cooperative games, people work together to win. Games can be infinite (prolong existence) or finite. Games can be goal-seeking or non-goal directed (like jazz). Agile is goal-seeking, finite, cooperative group game.

Every came has 3 stages:

1. Open (divergent): Set the stage, develop themes, ideas, information
2. Explore (emergent): Examine, explore, and experiment
3. Close (convergent): Conclusions, decision, action

In agile, the open is divergent and non-jugdmental. Exploration is emergent- create conditions where unexpected, surprising, and delightful things emerge. Subteams might explore and present back to the group. It can feel chaotic and directionless for those not used to it. Keep the creative tensions and suspend judgment as long as necessary. Be increasingly concrete. During the closing, bring in critical thinking and rigor. Select the most promising ideas for whatever comes next.

### Getting Started

Early on in a project, the whole team should work together closely to build a common language for the domain. Later on, smaller groups can leverage that language to collaborate and their output will be comprehensible to the rest of the team.

The path to the goal is not clear, and the goal may change. There are no "requirements"; only unvalidated assumptions. Delivering MMFs validates or invalidates our assumptions, and allows us early data to change direction with. A fuzzy goal is one that motivates the general direction of the work, without blinding the team to opportunities along the journey.

Put BDD work in a "slow lane" for features while you're learning it. Let early adopters take those. Once it's no longer slower, make it part of the definition of done for every story.

Start with a happy path feature. Good examples put you in the user's shoes and build empathy for what they're trying to do.

### Example Mapping

* Pink stickies: Discussions about examples usually lead down distracting side tracks because reality is complex and interlinked. Put those in a "parking lot"- they're worth talking about, just not right now.
* Yellow stickies: Stories
* Green stickies: Examples
* Blue stickies: Rules

### Personas

A persona's biggest benefit is not to tell us what to include, but to tell us what not to

### Feature Files

Feature files are intended to be "executable specifications", as well as the living documentation of the software. They obviate requirements docs, test plans, and regression tests. They shouldn't be tied to particular UI elements.

### Resistance as a Resource

People aren't actually resistant to change; they make change all the time, and would probably change plenty of things if they won the lottery. People resist changes where they don't see a likely net positive outcome. Ask yourself: What do they know that I don't know?

Layers of resistance:

1. We don't agree about the extent or nature of the problem (everything is fine and nothing needs to change)
2. We don't agree about the direction or completeness of the solution (this won't solve anything)
3. We can see additional negative outcomes (this is going to cause a bunch of new problems)
4. We can see real obstacles
5. We doubt the collaboration of others

Start at the first point and stop where the resistance begins. You may disagree about the nature of the problem, or they've seen something like this fail in the past. See what you can learn from this. If you can overcome these objections, this person will be your biggest supporter.

## Formalizing Examples Into Scenarios

Generating examples should be both divergent and exploratory, formalizing them should be convergent: converge on a single example and a precise set of words to describe it.

A feature file is a collaboration point, a springboard for conversation. It should not describe a test plan or technical details- it should describe how a user expects the feature to work. If feature files aren't used as collaboration tools, they're just added work. Typing code isn't the only thing that's work- talking about the feature is work too. They change and evolve over time- you don't just write a feature file once, polish it, and then move on to the next phase.

Storing feature files in your version control system gives you a history of the features.

Features aren't 1:1 with stories: Just describe the feature, it may shift and go across some user stories in the process.

### Agile Testing Quadrants

[Agile testing quadrants](https://lisacrispin.com/wp-content/uploads/2011/11/Agile-Testing-Quadrants.png)

* Business-facing tests that critique the product look at something that already exists. This is what is traditionally thought of as testing. Failing tests in this quadrant tend to become new BDD examples. Most teams have decent coverage here.
* Business-facing tests that support the team are written first, and act as specifications. This is where BDD lives. Most teams have nothing here.
* Technology-facing tests that critique the product are usually some kind of tool-assisted tests run in production-like environments. Most teams have a little action here.
* Technology-facing tests that support the team are typical TDD. TDD is a small loop inside the bigger BDD loop. Most teams have some occasional stuff here.

BDD will allow dedicated testers to spend more time in tests that critique the product.

### Meaningful Variations

Once you have your happy path, find the meaningful variations.

* Where are all the things that could be different in the happy path?
* Which variable is most likely to change?
* What's an example of a change that could cause a different outcome?
* Where are the boundaries of that change? Explore both sides.
* What could go wrong? Is there a value for one of the variables that breaks something? What should happen?

Are your variations relevant and valuable? Don't clutter your documentation with unlikely edge cases.

### Gherkin

Gherkin is a pidgin language that both computers and humans can understand. It helps collaboratively describe examples of business scenarios and thus define the expected system behavior.

* Feature title and description
* Scenarios - The core of gherkin, a concrete feature in action
  * Title - Usually no more than 5-6 words, expresses what makes this scenario different than other scenarios in a feature. It will be outlined under the feature title in the test runner.
  * Given - Any needed context
  * When - The main action taken in the scenario
  * Then - The change in the state of the system
* Data
  * `"""` - String blocks
  * `| |` - Tables
* Scenario Outlines - Similar scenarios that differ only in data. Easy for programmers to overuse at the cost of concrete readability by non-programmers.
* Backgrounds - If every scenario in the feature has the same Givens

It's common to see the same When step reused with different Given/Thens. The same action taken in different contexts often produces different results.

## Automating Examples

The test first mindset:

* I wish that things were different
* Prove that they're not the way you think
* Prove that they are now

Step definitions are interchangeable: When/Given/Then are just for readability, they'll match anything with the same language.

### Cucumber Expressions

Passing in strings:

```javascript
When I search ebooks for "Dune"
When("I search ebooks for {string}")
```

Other built-in types:

* {word} - Matches a single word
* {int} - Positive and negative integerse
* {float} - Floating-point numbers

You can create custom types for, eg. different types of users, objects, etc. You need to match these with regex.

### Testing Stack

Feature File -> Step Definitions -> Test Helpers -> Automation Framework

Eg: Gherkin -> Cucumber -> Helpers -> Capybara

* Gherkin and Cucumber are not web-specific- Using different helpers and automation frameworks would work for CLI apps, etc.
* Cucumber is for customer-facing tests, mocha et al are for developer-facing tests. Either tool can be used at any layer of the testing pyramid. You can do Given directly on persistence, When on the UI, and Then in the logic layer. This requires good decoupling, though.
* Not every step definition should go through the UI. If you have at least one, you can increase speed by hitting the services directly. You can tag these scenarios separately. Gherkin exposes system behavior to stakeholders, it doesn't dictate what's being tested.

### Product Workflow

The reason to start with a feature file before a UI is that it documents the desired behavior, which informs the visual design. The visual design might uncover features, and the feature file might uncover new UX dillemas.

1. Shared understanding
2. Feature file
3. UX/UI + Devs sketch out the macro parts of the layout, agree on ID names
4. Generate a quick and dirty annotated mockup together (contract between step definitions that use the UI and the UI)
5. UX/UI refine design while devs work on feature implementation

It's ok to make some assumptions that turn out to be wrong.

### Pairing BDD Example

* Run cucumber with no specs or application files
* Copy output into a spec
* Write pseudocode in comments in the first step
* Replace comments with first part of the first step definition
* Get a red test
* Do the minimal amount to make it green
  * Write a small amount of code
  * Assert that the result isn't blank
  * Hard code the answer
* Make it real with TDD
* Implement the actual design
* Refactor

It's common to hard-code the first response, and flesh it out as it becomes more complicated.

## Frequent Delivery and Visibility

You should get the product to a stable, "done" state multiple times a day. Waterfall aims to get to that state at the end of the project, scrum aims to get to that state at the end of the sprint, BDD aims to get to that state at the end of the scenario. The privilege of focus means that by not trying to get everything done at once, you get more done.

### What "testers" can do

* Asking questions when the team is exploring the behavior of new stories
* Asking questions when the known scenarios pass and you need to discover new scenarios that should pass but don't yet

They move to more high-value work, instead of routine work that's easily automated. Instead of only doing manual regression testing, testers can do exploratory testing: "Simultaneously learning about the system while designing and executing tests, using feedback from the last test to inform the next. Find new scenarios around the edges of the system's current behavior. Only add new scenarios for things that don't work as expected.

Have a dedicated environment for automated tests that won't interfere with exploratory tests.

### Gherkin Tips

* Aim for symmetry between your Givens and Thens
* Refactor shared setup to a background step

### Legacy Systems

"Integrate and Strangle":

Augment existing systems by extending them rather than modifying them. Wrap them in services to isolate your work from the existing system. Over time, the new system can replace existing behaviors and "strangle" the old system, but the system still works at every step of the way.

### Adoption Challenges

Change takes patience. Look for:

* Siloing tends to creep back
* New skills that work with a coach are harder to do when the coach leaves
* Developers will start taking on too much WIP and not collaborate
* Analysts will revert back to handing the team "requirements"
* The team will find some stories hard to split, so they'll stop trying
* The team will get hung up on test framework details

## Making Scenarios More Expressive

Scenarios should read as sentences. If you would be running out of breath or dying for punctuation, it's probably too long. Ask yourself how you would summarize all the steps using business language. That's a concept you need in your domain.

Scenarios shouldn't be so vague they're essentially tautologies. Look out for words like "valid", "correct", or "successfully." Fix this by asking "for example?" and "what's another example?" and "what would an incorrect result look like?"

Don't put implementation details like buttons and clicks into the feature file, and generally keep technical language out. You should be able to completely redo the UI without changing the feature file.

Look out for steps that have a lot of quoted strings and tables. Ask if it's really necessary to know all of these things for this example. If you take it out, does the example still work? Does it differentiate it from other examples?

Clarity and expressiveness is more important than reuse.

### Ubiquitous Language

From Domain-Driven Design. You need a powerful mental model for your domain. You shouldn't have to translate layers of domain concepts between business and technical representations.

> If we mean the same thing, we should write it in exactly the same way. If we write it the same way, we should mean exactly the same thing.... If one word is different, then they should know that one-word difference is significant, and they must understand the difference before they implement it.

### Gherkin Language

* Given steps should be passive voice. They describe things that just are, so we don't care about how they got that way.
* When steps are about action, so they should be present-tense and active.
* Prefer writing first-person to help develop user empathy. For example:

```gherkin
Given I'm library patron Chandra Khan 
When I log into my library account
```

* You can use third-person when describing multiple people (like a chat app)
* Then steps should contain the word "should" for a preference, and "expect" for an expectation

```gherkin
Then my account should be reinstated
And I expect to be fined $1.00
```

* Then steps can either include the actor or make a statement about the system. Use whichever feels more natural.
* Aggressively fine-tune and delete filler words. Go for concise language.
* If you're talking an entity with attributes, use a table
* Consider how a nontechnical user would write the step
* The step should still work if you totally changed the underlying technology
* Consider combining multiple technical steps into one domain actions (eg. "Searching for a book")
* A scenario title should answer "What is this particular example intended to illustrate?"

```gherkin
Feature: Ebook Search
  Scenario: By author - Complete last name matches
```

## Growing Living Documentation

"Dead" documentation is a snapshot in time, but isn't necessarily connected to the feature itself. Living documentation is executable.

New, unrelated behaviors should not break old scenarios.

Feature files replace:

* Requirements specifications
* Detailed test plans, cases, and scripts
* Traceability docs (in regulated environments)

They do not replace:

* Design docs and mockups
* Data dictionaries and glossaries
* Guides
* Support tools

Keep Gherkin language out of your stories. User stories are told, not written; don't formalize them until you have to, just stay in conversation, write free-form, and focus on learning.

MMFs and user stories are planning artifacts; don't tie them too closely to feature files. Planning artifacts are transient and ephemeral, feature files are living documentation. Organize feature files by business function.

If the behavior changes, the scenario should change. Otherwise, it shouldn't.

Split a feature file when:

* Backgrounds change
* A new domain concept emerges

Use tags as a secondary level of organization.

* Tag things that require particular services or infrastructure to be running
* Tag things that are especially slow
* Tag things that are unreliable

Keep the structure of your docs emergent!

## Succeeding With Scenario Data

Good scenarios are:

* Independent
  * No state dependencies
  * Able to run in any order
* Repeatable
  * Identical results with every run
* Researchable
  * Something better than "expected true, got false"
* Realistic
  * Actual examples, no "User A", etc.
* Robust
  * Tests don't break due to unrelated changes
  * Tests aren't dependent on infrastructure and side effects
  * Decouple date and time
  * Give the test scenarios their own environment to run in
* Maintainable
  * Can be understood and modified by someone other than the person who wrote it
* Fast
  * Fast tests get run more often and tighten the feedback loop

Only use enough test data for the examples in your app.

When you have to change your scenarios to accomodate a refactor, change your Then steps first and work backward.

Choose a "test data curator" to own and manage the test data for the application.

Data can be shared or scenario-specific. Create shared data for:

* When a background step performs the same data setup for all the scenarios in a file
* When the data for the scenario obscures the behavior you're trying to test
* When you have domain-specific data:
  * Lists of companies
  * Lists of products
  * Important date ranges
  * Standard weather and terrain conditions

"Data Personas" are standardized sets of data:

```gherkin
Feature: Data persona definitions

  Scenario: Jennifer the researcher
    When I'm Jennifer
    Then I should have only the following office:
      | Room Number | AB 123 |
    And I should only have the following lab:
      | Room Number | AB 124 |
    And I should only have the following research animals:
```

These feature files can serve as glossaries for your data personas and also executable, so they assert that they still work correctly.
