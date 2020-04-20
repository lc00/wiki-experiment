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

### Testing Stack

Feature File -> Step Definitions -> Test Helpers -> Automation Framework

Eg: Gherkin -> Cucumber -> Helpers -> Capybara

* Gherkin and Cucumber are not web-specific- Using different helpers and automation frameworks would work for CLI apps, etc.
* Cucumber is for customer-facing tests, mocha et al are for developer-facing tests. Either tool can be used at any layer of the testing pyramid. You can do Given directly on persistence, When on the UI, and Then in the logic layer. This requires good decoupling, though.

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

It's common to hard-code the first response, and flesh it out as it becomes more complicated.

## Frequent Delivery and Visibility

## Making Scenarios More Expressive

## Growing Living Documentation

## Succeeding With Scenario Data

## Conclusion

