## Overview

A user story is:

* **Card**- A written description, for planning and as a remdiner
    * A story _represents_ requirements, it doesn't _define_ them.
    * The appropriate size for a story is between half a day and 2 weeks of work for one or a pair of developers.
    * These should be written in the language of the business.
* **Conversation**- Where the details get fleshed out
    * These are not contractual obligations, they're a shared understanding
* **Confirmation**- Acceptance tests that capture details and verify when it's done
    * These should be jotted on the back of a card as short, incomplete reminders

Anyone, especially customers, can/should write stories.

### The Process

1. Gather user roles
2. Note key personas
3. Initial story-writing workshop
4. Estimate initial stories with planning poker
5. Select iteration length
6. Estimate velocity
7. Prioritize stories
8. Allocate stories to iterations
9. Write acceptance tests

### Prioritizing

You can prioritize a story because:

* Its desirability to a wide base
* Its desirability to a small number of important users
* Its cohesiveness in relation to other stories

### Why stories?

* Stories emphasize verbal, rather than written communication
    * Writing implies an unearned precision
    * A story is really just a promise to have a conversation
* They are comprehensible to everyone, not just developers
* They're the right size to plan with
* They work for iterative development
* They defer detail until you need it

## Writing Good User Stories

A good user story is:

### Independent

* Don't have stories where estimates would depend on what order they're accomplished in (eg. one for Visa, Mastercard, AMEX)
* Either combine or split differently (eg. One credit card, additional credit cards)

### Negotiable

* Be intentionally abstract with your documentation
* Resolve details as tests, not documentation

### Valuable

* Either to a customer or a user
* _Not_ to developers
* No tech stuff, no UI assumptions (eg. "When a user clicks on a button...")

### Estimatable

Drivers of non-estimability:

* Devs lack domain knowledge
* Devs lack tech knowledge
* Story is too big

Use time-boxed spikes to learn just enough to estimate.

### Small

* Big and small stories are both hard to plan with

#### Splitting

Big stories are either compound or complex.

* For compound stories, split along data rather than CRUD actions (eg. "A user can add and edit a car")
* For complex stories, spike in one iteration, implement in another

#### Combining

Combine all small work into one, named story.

### Testable

* Aim for 99% automation, not 10%
* Use measurable criteria in your story description

## User Role Modeling

In no more than one hour:

1. Brainstorm an initial set
    * 15 minutes
    * Write a role, read it out loud, post it
    * Use physical cards
2. Organize the initial set
    * Group the cards
    * Use the amount of overlap the roles have to literally overlap the cards
3. Consolidate the initial set
    * Consolidate things that completely overlap
    * Use joining cards to consolidate roles
    * Split cards that have 2 versions
    * Rip up any role that's not important to the success of the system
4. Refine the roles
    * A user role is one person, not a group of people or a company
    * Experiment with using extreme characters
    * Declare the attributes of each role
        * Frequency of use
        * Domain expertise
        * Computer proficiency
        * Proficiency with this software
        * General goal- Convenience, rich experience?

Use your user roles in the story description. You can build personas for key roles, but not every role needs one.

## Gathering Stories

"Capture" and "elicit" imply that you can/should get all requirements up front. What you're really doing is "trawling" with different sized nets at different times. Like fishing, it also implies that some requirements might die, you won't catch every one, you'll catch some garbage, and it takes skill.

* The relevance of a story changes over time
* It's ok to have broad, high-level stories early on

Tools:

### Interviews

* Use real users when possible
* Don't ask them what they need, they don't know
* Ask open-ended and context-free questions

### Questionnaires

* User for prioritizing, but not trawling

### Observation

* Take every chance you get to observe users

### Workshops

* Goal is to write as many stories as possible
* _Don't_ talk about screens and fields, it's more about conceptual workflows and lo-fi prototyping
* Erase prototypes when you're done
* Ask questions:
    * What will this role want to do next?
    * What mistakes could they make here?
    * What could confuse the user at this point?
    * What additional info could the user need?

## User Proxies

A user proxy is never as good as a real user.

* **User's manager**-  Usually a poor bait & switch. They often don't know anything useful.
* **Development Manager**- Bad- they usually have conflicting priorities.
* **Sales People**- Use as a conduit to users- have them introduce you.
* **Domain Experts/SMEs**- Good for helping to develop a domain model and business rules. Not necessarily a good source for stories unless they're also users.
* **Marketers**- Understand markets, but not necessarily users. They can help with prioritization, likely wants quantity of features, not quality.
* **Former users**- Good proxy if recent
* **Customers**- Their needs are important and need to be balanced with the needs of the users. Sometimes the users still just know better.
* **Trainers and Supporters**- Likely to advise making software that easy to train on or support
* **Business/Systems Analysts**- Can be good, but beware analysis paralysis.

Tricks:

* Create a user task force that a proxy can use
* Average multiple proxies
* Use competitors as proxies
* Beta early

## Acceptance Testing

* Capture details and assumptions in tests
* Use them to tell you when something has been implemented
* Write tests:
    * Whenever customers and devs talk
    * At the beginning of an iteration
    * As details are discovered during and after programming
* Ask these questions about a story:
    * What else do programmers need to know?
    * What am I assuming will be implemented?
    * Are there circumstances when this will behave differently?
    * What can go wrong?
* Tests need to be specified by customers, even if they're written by devs
* Write as many tests as adds value- capture tiny details with unit tests
* Fit/FitNesse are good acceptance testing tools
* Testing is about bug elimination- don't obsess over coverage
* Also test:
    * UI Tests for interface components
    * Usability
    * Performance
    * Stress testing

## Guidelines for Good Stories

* Start with each role's goal for the software
* "Slice the cake"
* Write stories for a single, closed task (not an ongoing one)
* Keep track of constraints separately (definition of done)
* Make stories tighter closer to their implementation horizon
* Keep the UI out of the story
* Not everything has to be a story- UI docs, etc.
* Use the role in  the story label- "As a _role_, I want _feature_, so that _benefit_"
* Write as one user
* Write in active voice
* Customer should write stories
* Don't number them- give them short names if needed
* Only use them as reminders to talk

## Estimating User Stories

* Use ideal developer days, relative complexity, or smallest unit of work as baseline
* Estimate should include conversations, testing, etc.
* Planning poker
* Triangulate estimates by comparing similar point values
* Central limit theorem: The sum of independent samplesl is normally distributed
* Precision decreases as size increases

## Release Planning

* You can fix a date easily, but what will be included in the date needs to stay loose
* Plan releases around themes
* MoSCoW- Must, should, could, won't this time
* Cost changes priority
* You can split a story if parts need to be prioritized differently
* You can increase priority to better understand a risk
* For infrastructure choices, write a story that forces the choice
* Shorter iterations are preferred, but have an overhead
* Initial velocity can be historic, based on the first iteration, or 1/3-1/2 the ideal dev-days
* Allocate stories to iterations by point value/velocity into releases

## Iteration Planning

1) Discuss a story
2) Split the story into tasks
3) One dev accepts responsibility for each task and estimates the task in hours
4) At end, check for anyone being overcommitted

* Splitting tasks allows multiple devs to work on a story
* Commitments are fluid and can change during project

## Measuring and monitoring

* Don't count partially completed stories
    * Use smaller stories
    * There's always a lot of hidden complexity after "90%"
    * They don't represent any value
    * Implies a false precision
* Don't retroactively change point values

Chart:

* Actual vs. planned velocity
* Cumulative actual vs. planned points
* Burndown for each iteration
    * Adding stories doesn't look differently than stalling
    * This shows overall progress
* Burndown for each day in an iteration
* Use big, visible charts

## What stories are not

* IEEE 830
    * Tedious, error-prone, unreadable, doesn't actually tell you what it does
* Use cases
    * Too complicated, long-lived artifacts, hide interface details in them
* Scenarios
    * Too narrative, not a conversation

## Why stories?

* Emphasize verbal communication
* Comprehensible by everyone
* Right size for planning
* Work for iterative development
* Encourage deferring detail
* Support opportunistic development
* Encourage participatory design
* Build up tacit knowledge

## Story Smells

* **Too small**- Estimates vary wildly based on order
* **Interdependent**- Recombine, resplit
* **Goldplating**- Agile has low WOW-effect, actively watch for devs doing this
* **Too much detail**- Use smaller cards
* **UI Details in card**
* **Thinking too far ahead**- trying to bring back Big Requirements Up Front
* **Customer can't prioritize**- Stories are too big
* **Customer won't write or prioritize stories**- They'll try to avoid responsibility, say that it's ultimately yours

## Scrum

Rules:

1. Have a sprint meeting at the start of a sprint
2. Each sprint must deliver working, tested software that demonstrates something of value to end-users or customers
3. The product owner prioritizes the product backlog
4. The team decides the amount of work to be brought into a sprint
5. Once a sprint begins, only the team may add work to the sprint backlog
6. The product backlog can be added to or reprioritized at any time
7. Short scrum meetings are held every day
8. Only active participants can speak during a scrum meeting
9. The result of a sprint is showed at the sprint review- no slides allowed
10. No more than 2 hours can be spent prepping for a sprint review

## XP

### 12 Practices

* Small releases
* The planning game
* Refactoring
* Testing
* Pairing
* Sustainable pace
* Team code ownership
* Coding standards
* Simple design
* Metaphor
* Continuous integration
* On-site customer

### 4 Values

* Communication
* Simplicity
* Feedback
* Courage

### 5 Principles

* Rapid feedback
* Assuming simplicity
* Incremental change
* Embracing change
* Doing quality work

## Additional topics

### Non-Functional Requirements

* Perfomance
* Accuracy
* Portability
* Capacity
* Revisability
* Maintainability
* Interoperability
* Availability
* Usability
* Security

Use constraint cards and append them to stories.

### UI

* Keep it out of cards
* You can do some interface design up front to develop look and feel
* Try not to change it much once you're deployed

### Bugs

* Can keep on different colored cards
* Combine all bugs in an iteration into one story
