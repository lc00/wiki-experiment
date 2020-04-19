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

## Formalizing Examples Into Scenarios

## Automating Examples

## Frequent Delivery and Visibility

## Making Scenarios More Expressive

## Growing Living Documentation

## Succeeding With Scenario Data

## Conclusion

