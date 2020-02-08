## Inception

10 questions to align the team for 3-6 months.

Big picture (Why):

* **Why are we here?** - Who the customers are and why you decided to do this project in the first place. Go to the gemba and see for yourself. What's "the commander's intent"? There are a lot of possible reasons for doing your project, which ones matter?
* **Elevator pitch** - Describe the project in 30 seconds, using this format (from Crossing The Chasm):
> For `<target users>` who need `<job to be done>`, the `<name of product>` is a `<product category>` that `<key benefit>`. Unlike `<existing competing solution>`, our product `<primary differentiation>`.
* **Product box** - What's the ad say and why would you buy it? Focus on benefits, not features. Create a slogan, put it on a box.
* **NOT list** - Increase clarity by being explicit about what you're not doing. What's in, what's out, and what's unresolved?
* **Meet the neighbors** - Who are the other internal stakeholders? Security, infrastructure, support, technical writers, marketers, database administrators, etc..

Solutions (How):

* **Show solution** - Draw some blueprints to make sure every understands the problem well enough. When you pick your team, you pick your architecture: People will gravitate to what they're good at.
* **Up at night** - What parts of this are unknown or scary? Identify the things that could go wrong, think about how to stop them from happening, move on. Which risks are worth tackling, which ones are not?
* **Size it up** - Is this a 3, 6, or 9 month project? Project failure radically increases over time, so keep the projects short (no more than 6 months).
* **What's going to give** - Time, scope, budget, quality. What's least important for the project right now? In agile, time, quality, and budget are fixed. The thing that flexes is scope. Rank the qualities and goals of the product in order of importance.
* **What it going to take** - What do we need to pull it off? One hour of customer time per day, one feedback session per week. Customer has to be willing to do this and have the authority to make decisions. Who is on the team, who are the decision-making authorities, how much is it going to cost?

This should be visible in the work space, and updated as it changes.

## Why you can't communicate with documents

"I didn't say she took the money"

These all mean different things:

* **I** didn't say she took the money
* I **didn't** say she took the money
* I didn't **say** she took the money
* I didn't say **she** took the money
* I didn't say she **took** the money
* I didn't say she took **the** money
* I didn't say she took the **money**

## User Stories

* **I**ndependent
* **N**egotiable
* **V**aluable
* **E**stimatable
* **S**mall
* **T**estable

Constraints: Speed, design, etc.

Draw lots of pictures (flowcharts, personas, scenarios, system maps, process flows, concept designs, storyboards, paper prototypes), and use the pictures to extract stories.

A release is a "minimal marketable featureset"- a group of related stories that are of value to your customers.

## Estimation

* "Cone of uncertainty": Variability is higher at inception than it is close to the deadline
* Humans are good at relative estimation, but pretty bad at absolute estimation
* Use example small, medium, and big stories as reference points when sizing
* Planning poker uses the wisdom of crowds
* Don't size anything higher than 5
* You can flexible on release date or flexible about features
* Change is always there- there is no fixed scope+time+budget+quality project, you only choose whether you acknowledge the change or not

## Iterations

* Burn down chart vs. Burn up chart (total scope is at the top, changes in it are easy to see)
* Analyze one sprint ahead. Just enough artifacts:
  * Flow chart
  * Personas
  * Paper prototypes
  * Acceptance tests

Things you need before you can really start building stories (iteration 0):

* Source control
* Automated builds
* Dev and test environments
* Architectural spike

### Rituals

* **Story Planning Meeting**: Make sure that the stories and acceptance criteria for the next week are ready with the customer
* **Iteration Planning Meeting**:
  * **Showcase**: Demo last iteration's stories with customer
  * **Plan Next Iteration**: "Weather forecast", use your burn-down chart ("bad news early")
  * **Mini Retro**: 10-15 minute reflection on what you're doing well, and what you can do better
    * Retro Prime-Directive: "Regardless of what we discover, we understand and truly believe that everyone did the best job they could given what they knew at the time, their skills and abilities, the resources available, and the situation at hand." It's not a witch hunt.
* **Standups**: Make public commitments to each other.

### Workspace

* Inception deck posted
* The release wall (shows which stories have been completed on the left, backlog on the right)
* The story board (not started, in progress, ready for review, done)
* Velocity & Burn Down
* Working Agreements
  * Hours
  * Stand-up time
  * Done includes testing
  * Respect the build
  * When someone asks you for help, say "yes"
  * Weekly demo time
  * Time the customer is available
* Shared Values
  * We don't cut corners
  * No broken windows
  * It's OK to disagree
  * We can handle the truth
  * Don't assume, ask
  * When in doubt, write a test
  * Crave feedback
  * Check your ego at the door
* Domain language (eg. what does "location" mean?)

## Engineering Practices

Capture bugs as tests before you fix them- It helps guarantee you understand the nature of the bug and keeps it from showing up again, or that someone else doesn't reintroduce it

Refactoring make the cost of change less. Technical debt (shortcuts, hacks, duplication, complexity, spaghetti, etc) make it expensive. Refactoring should take place on the order of minutes rather than days. Same with CI.

Write your tests as if your code already exists.

Things that can go wrong in deployments:
* Human error, fat fingers, and bugs
* Miscommunication with other teams
* Errors in configuration files
* Differences in environments
* Out of date documentation

After your tests pass, merge in the latest code to check for differences.
