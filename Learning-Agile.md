## Learning Agile

* Do you understand the principles first, or adopt the practices and hope an understanding of the principles will develop?

### The Stand-up Mindset

Where stand-ups go wrong:

* The PM is worried about people deviating from their plan, so they focus on getting everyone's status. They get mad that they only find out about problems when it's too late to do anything about it.
* Devs don't want to go to another meeting. They tune and say as little as possible so they can get back to work

If the project was collectively planned, the PM doesn't have to worry about deviations from _their_ plan, and might better understand that the plan everyone came up with together might need to change. The standup becomes a chance for everyone to learn something from each other and come up with better plans.

## Understanding Agile Values

Agile is a set of methods and methodologies that your team think more effectively, work more efficiently, and make better decisions. It's the ability to handle change. It involves project management + software design and architecture + process improvement, and it's also a mindset.

The Waterfall Process:

* Requirements
* Design
* Implementation
* Verification
* Maintenance

Described by Winston Royce from Lockheed in 1970 in response to a "software engineering crisis" resulting from common problems. "Planning the work and then working the plan" causes problems through overly rigid documentation, poor communication, and bugs. Project managers get held accountable for out-of-date plans. The best waterfall teams usually have in common:

* Consistent communication between users, managers, and executives throughout the project
* Good practices (code reviews, automated testing, defect prevention)
* Drawers full of documentation that had never been opened (the thought that went into them was the important part

These are also common the best agile teams.

### Initial challenges with going agile

Better than-not-doing-it results:

* Devs make technical sacrifices to keep the schedule
* PMs feel blind because they can't see ahead on the roadmap, reacting rather than planning, coordinating rather than controlling, collecting statuses and relaying them to stakeholders
* Account managers feel like they have to be a full-time part of the team, answer a lot of questions, and go to a lot of meetings

This is the result of fractured perspectives on many agile practices. Each stakeholder views the purpose of a practice  slightly differently. User stories aren't just Gantt charts on a whiteboard, and everyone's roles change a little. Some people are giving up control that they are accustomed to, others are taking ownership they didn't have before. If everyone only focuses on their tasks, the team as a whole is at a disadvantage. The agile elephant is bigger than the sum of all of its individual practices.

Largest sources of failure with agile projects (VerionOne State of Agile survey):

* Lack of experience using agile methods
* Company philosophy at odds with agile values
* External pressure to follow waterfall practices

### The Agile Manifesto

* **Individuals and interactions over processes and tools**: People can go wrong blindly following a process, and the wrong tool just helps them do the wrong thing faster. This is supported by standups, retros, and user stories.
* **Working software over comprehensive documentation**: Use documentation that actually helps people make the software, and actually making the software is a good way to make sure that things are on track. Documentation can be good without being comprehensive. This is supported by TDD. Comprehensive documentation is always biased by the author's perspective, and ends up with a fractured perspective.
* **Customer collaboration over contract negotiation**: No SLAs, no finger-pointing. Embed a customer representative on the team.
* **Responding to change over following a plan**: If you work the wrong plan, you'll build the wrong product. It takes work to change a plan, so people resist it. This is supported by task boards.

> Without concrete practices, principles are sterile; but without principles, practices have no life, no character, no heart. Great products arise from great teams--Teams who are principled, who have character, who have heart, who have persistence, and who have courage.
- Jim Highsmith

### Methodologies

**Scrum**:

* Make a prioritized list of features (product backlog)
* Each month, pull off the top of the list (about one month's worth), and promise to deliver in a month
* Every day, meet for 5-10 minutes
* Make one person the scrum master, and make it their job to remove roadblocks

**XP**: Produce deployable software every week. In each iteration, the team analyzes, designs, codes, tests, and deploys a subset of features.

Scrum and XP are both timeboxed and iterative. Timeboxing helps users know when they can expect new features to be delivered.

**Lean**: Mindset (not a methodology) about reducing waste.

**Kanban**: Method for improving process, built on lean.

## The Agile Principles

Give customers what they need, not what they ask for. Over the course of a long project, there's a high likelihood of the external environment changing and obviating some of your plans. If an ebook reader takes a year and a half to develop, there's a good chance the reader the market needs in a year and a half isn't what you would have come up with at the beginning. If you build an architecture than only works with one version of the master plan, you end kludging around any changes.

The principles aren't a menu to choose from- they all work together. It's not just the way you build software, but also how you interact with each other and the rest of the company.

If you're a rock-star developer used to working all alone, this will prevent your perfect designs from getting ruined when the customer changes their mind. You get to ask tough questions up front and throughout the project, you make sure that the only meetings and documentation are the ones that help make better software, and you get a chance to learn from your team by collaborating more closely.

If you're a project manager who is...

* In the weeds, and does lots of schedules and estimates and day-to-day stuff, you should be a scrum master
* A product expert and analyst, you should be a product owner
* A supervisor who works with upper management a lot, you should be an agile champion

### Delivering the project

* **Our highest priority is to satisfy the customer through early and continuous delivery of valuable software**: Releasing software early, delivering value continuously, and satisfying the customer are 3 different things that work together. Dealing with customer panic over early versions of software can be dealt with by emphasizing collaboration and flexibility, and by building trust through the continuous delivery.
* **Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage**. Why are changes to projects so emotionally charged? Until the change, you thought you were doing a good job, and when a customer changes their mind it feels like they're disrespecting your work. But customers didn't intentionally send you down the wrong path. It might even be embarassing for them to admit that. Your deadline might be blown, but so is theirs. You're being asked to read the customer's mind, they're being expected to predict the future. Don't blame, no one's in trouble when something changes, don't sit on changes, don't view changes as mistakes, and use everything to learn.
* **Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale**: Agile deals with the chaos of changing requirements by working iteratively and delivering frequently. The frequent deadlines allow the team to stay on track and get lots of feedback early.

### Communicating and working together

* **The most efficient and effective method of conveying information to and within a development team is face-to-face conversation**: Conversations lead to deeper understanding and better retention. Teams generally rely on conversations anyway since documentation has always been such a poor communication tool.
* **Businesspeople and developers must work together daily throughout the project**: The input of business people is important for understanding what the software should do and what parts of it are most valuable. They are critical members of the team.
* **Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.**: The team needs to know why the project matters. Performance reviews that punish bad code and reward clean code just stop bad code from being found, rewarding bug counts leads to antagonistic relationships, and rewarding the amount of documentation generated leads to bloated docs. Cover-your-ass roles lead to contract negotiation between people rather than collaboration. Developers spend time on protecting themselves and insulating against change.

### Project execution

* **Working software is the primary measaure of progress**: Status reports are vague are don't actually communicate how much has been done very well.
* **Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.**: The hard-and-fast deadline is the first tool in the command-and-control manager's toolbox. After a week of crunching the team starts doing less work, and all of it is lower quality.
* **Continuous attention to technical excellence and good design enhances agility**: Avoiding bugs is faster than fixing them.

### Constantly improving the project and the team

* **Simplicity--the art of maximizing the amount of work not done--is essential**: Deleting code is not destructive, like "deleting" a wall in construction is. Getting back an old piece of code from a version control system is not a big deal. Reducing the amount of dependencies a piece of code has makes it stronger because it's another thing that doesn't need to be maintained.
* **The best architectures, requirements, and designs emerge from self-organizing teams**: Instead of an architect making one big design up front in isolation, the whole team contributes to the architecture. This is harder for architecture specialists, but more rewarding and better for the team. Incremental architecture is a better fit for the project and leads to stronger overall design.
* **At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly**: This requires having time blocked out to do it, and a willingness to speak freely.

## Scrum and Self-Organizing Teams

> For Scrum to work, the team has to deeply and viscerally understand collective commitment and self-organization. Scrum's theory, practices, and rules are easy to grasp intellectually. But until a group of individuals has made a collective commitment to deliver something tangible in a fixed amount of time, those individuals probably don't get Scrum. When the team members stop acting as many and adopt and commit to a common purpose, the team becomes capable of self-organization and can quickly cut through complexity and produce actionable plans.
- Ken Schwaber

Everyone on a Scrum team owns the project. It's natural to CYA wash your hands of decisions someone else made, like scheduling and assignments. There isn't a role for someone who "owns the plan." Scrum masters guide the decisions and make sure they're philosophically sound, but doesn't make decisions for the team. Product Owners understand the business value of what's being delivered, and is the voice of the business for the team. The Product Owner gives broad strokes about what's being built during Sprint Planning, but there's not enough time for the level of detail needed during the actual project. The Product Owner needs authority to make decisions, and spends a lot of time working with stakeholders to get questions answered.

Rather than treat estimates like commitments you can nail people to, treat them facts that have yet to be uncovered. In the future, everything will have taken a certain real amount of time- we're trying to get to that truth faster. Don't motivate people with deadlines, or "ratify" estimates, or hold people accountable. It's a team thing. Figuring out who will do what is done throughout the sprint.

Iterative processes make progress through successive refinement. Incremental processes are where something is built and delivered in pieces. Scrum is both.

Don't have an "A team" that writes features and a "B team" that does maintenance and fixes bugs, or allow senior members to dump boring work on junior members. The person who creates bugs is best equipped to fix it, and the extra documentation and communication required to hand it off is waste.

A cruise ship is slow to turn, a team of speedboats is fast to turn but takes more communication and coordination. A team of firefighters pointing a hose at flames looks easy, but it takes practice and coordination to move as one unit.

Gantt charts give people a false sense of security with anticipating dependencies. The estimates and timing are always going to be off (especially since the person giving the estimate was likely overoptimistic and not corrected by anyone). Deal with project dependencies as they come up. Team members are more likely to be acutely aware of dependency problems because they're finding out about them scrum to scrum and identifying them while working on the project, not crystal-ball reading ahead of time.

By deferring planning until the last responsible moment, you're getting the same benefit as doing it up front but with more information.

### Why it's so hard for requirements to get through the chain of command correctly

* The PM scopes out the work with a document
* Managers sign off on the scope
* An analyst review the scope then talk to users and other stakeholders to understand their jobs
* The analyst comes up with use cases and functional requirements
* Programmers estimate the work
* The PM takes the requirements and estimates and builds a schedule, and reviews it with stakeholders and managers

### Collective Commitments

Our plans don't commit us, our commitments commit us. You can't make a commitment on behalf of someone else. Is someone assigned to a project and doing what they're told (chicken) or truly committed (pig)? Pigs care more about the success of the project than they care about anything else in their professional life- and sometimes that means blurring roles or using technologies you don't personally like. Chickens matter (eg. a user giving their opinion), but their professional success isn't tied to the success of the project. If someone (like the SM) "owns" the plan or there's a "single wringable neck", it encourages everyone else to be a chicken. The team committing to deliver the software means that you are taking accountability for delivering something even if you didn't personally work on it.

Elevating goals motivates people to want to commit. Digging a ditch isn't motivating; digging a ditch to protect your town from an imminent invasion is. Get people motivated by the impact of the software they write.

### Mechanics

#### Sprint Planning

A 2-part meeting, each part is time-boxed to 4 hours per 30 day sprint (proportionally shorter for shorter sprints). Beforehand, the Product Owner comes up with a prioritized backlog for the product that the stakeholders and users have bought into. In the first part, the team selects what items they will commit to delivering by the end of the sprint. In the second part of the meeting, the team figures out what tasks are a part of delivering those backlog items, which becomes the sprint backlog.

#### Daily Scrum

All team members must attend. Anyone else may attend, but isn't allowed to participate. Maximum 15 minutes. It's not a status update meeting, or a way for a PM to get the updates needed to manage the schedule. They help teams inspect the work (which helps maximize its value) and make decisions at the last responsible moment. Even with face-to-face communication, detail gets lost- the scrum gives a chance to sunshine it. Team members become familiar with each other's work, and help make it better ("Empirical process control"). Team members self-assign and negotiate tasks between themselves instead of being given them by a manager. A team will find "bugs" in the schedule in real-time faster than a project manager would be able to find them with an up-front plan. Take bigger discussion "offline." It's not a series of 1:1 conversations with each dev and the project manager, it's team members talking to each other.

Modified questions:

* What did we achieve yesterday on priority 1?
* What was our contribution to priority 1 worth in story points?
* What is our plan for completing priority 1 today?
* What, if anything, is blocking us or has the potential to slow us down today?

#### Sprint

No one is allowed to tell the team how to do their jobs. If a sprint is in danger, the team must tell the product owner as soon as possible so that expectations can be reset with stakeholders. More items can be added if the sprint ends early. In the case of catastrophe (eg. staffing problem), the product owner can terminate a sprint. This needs to be rare, or else the stakeholder trust will disappear. If something isn't done at the end of a sprint, it goes to the top of the backlog- never give the impression you've delivered value that you haven't.

#### Demo

The team demos only items that are done-done (nothing left to do). The team and the stakeholders share opinions and feelings.

#### Retro

What did we do well, what can improve in the future? Scrum Master is responsible for documentating them and adding to the product backlog as non-functional items.

### Scrum Values

* **Courage**: Push back against poor culture and shortcuts
* **Commitment**: Everyone is committed to the goals, and has authority to make decisions about those goals
* **Respect**: The teams foster mutual respect for each other, including non-technical team members
* **Focus**: No distractions or other assignments or committees during a sprint. Switching to other tasks when blocked introduces context switching.
* **Openness**: Standups, task boards, and retros don't give opportunities for CYA or plausible deniability.

### Product Owners

* Understands what the company needs the most
* Understands what features the team can potentially deliver
* Figures out which features are more or less valuable
* Figures out (with the team) which features are harder or easier to build
* Helps the team figure out which features to build in each sprint
* Helps the company figure out how to prepare for the next round of software

### Scrum Masters

* Help the team follow the rules of scrum and remove any impediments that are stopping them from doing so

## Scrum Planning and Collective Commitment

* Team members often gold-plate the software (with good intentions), and customers often request features that will never get used because they're incentivized to cram everything in now.
* GASPs (generally accepted scrum practices) include points, user stories, standing during scrums, etc.
* Organizations that refuse to fail are the least innovative and least fun.
* A lot of the tools seem similar to traditional project management tools, but the difference is in how they change, how often they're reexamined
* Agile teams plan broad strokes first (stories) and details last (tasks), and frees you from "padding" and CYA estimates
* For non-functional features, still think about how to demo them. What does faster look like?
* Bugs affect the burndown chart, and require things to get taken out to accomodate for them.
* Global teams are difficult, but not impossible. Consider colocating scrum teams, and having a scrum-of-scrums to keep them together.

### User Stories

* Effective for fighting gold-plating and feature bloat.
* Acceptance criteria is on the back of the card so that everyone knows when it's done
* Break down a story into individual tasks on different colored cards, and attach them to the original story card.
* If a product owner rejects something, they put it back in the "in progress" column with new task cards
* Stories that aren't finished in time are put back on the product backlog and reestimated for next sprint

### Story Points

1. Start with the most valuable user stories from the product backlog
2. Take the smallest story in that list and point it
3. Discuss how accurate it is- additional challenges nudge it up, reusing and scaling back nudges it down
4. Repeat until the sprint backlog is filled

Make an average size 3 points, the biggest valuable feature 5 points, the smallest one 1 point.o

Story points work because:

* They're simple to understand
* They're based on real-life
* The team controls them
* They get the team to talk about estimates
* Developers aren't scared of them
* They help the team discover the meaning of the story
* They help the team get committed by seeing how much work they've accomplished and how much they have left to go, as well as a tight feedback loop on underestimating

### Burndowns

* X is days in sprint
* Y is 120% of the total points for a sprint
* Draw a straight line from the total points in the sprint and 0 points at the end of the sprint
* Measure how many points are left every day (including ones that get added mid-sprint)
* Below the line is good, above the line is bad
* You may need to remove stories from the backlog before the end of a sprint to get below the line, which gives you an opportunity to communicate in advance with stakeholders

## XP and Embracing Change

Use working software as the basis for conversation, not documentation. Use it to drive conversations, get feedback, and make changes.

>> Programming practices by themselves are barren. Unless given purpose by values, they become rote. Pair programming, for example, makes no sense as a "thing to do to check off a box." Pairing to please your boss is just frustrating. Pair programming to communicate, get feedback, simplify the system, catch errors, and bolster your courage makes a lot of sense. - Kent Beck

XP practices allow you to confidently do rework without also introducing bugs, and to incorporate really good ideas if it makes sense to. BRUF sometimes works OK for the first release, maybe the second. By the third+ release, users want things to change, but to incorporate those changes parts of the system will need to survive redesign.

Quality isn't just about giving users what they ask for, it's about meeting their needs, even if it's not what they asked for.

### Programming practices

* **Pairing**: Two brains on the problem, keeps bugs from being built into the code, reduces fatigue, reduces temptation for shortcuts. It also normalizes code practices, and gets the best from each developer.
* **Test-first development**: Keeps bugs from being built into the code, ensures testable code. It also prevents CYA requirements-following and encourages developers to think about how the code is going to be used.

### Integration practices

* **10 Minute Builds**: Includes running the tests, short enough that people do it often
* **Continuous integration**: Reintegrate master frequently.
  * Pass a "build token" (like a rubber chicken) from pair to pair. When a pair gets the token, they integrate the latest changes

### Planning practices

* **Weekly Iterations**: Working through stories
* **Quarterly Themes**: Talk about the big picture, recurring issues, repair work needed, etc.
* **Slack**: Small stories added to the end, which get cut if the team runs out of time

### Team Practices

* **Sit together**
* **Informative Workspace**: Information radiatiors
* **Osmotic Communication**: Learning things through discussions that happen out in the open

### XP Values

* **Communication**: Everyone knows what everyone else is doing
* **Simplicity**: Developers focus on writing the most simple and direct solution possible
* **Feedback**: Constant tests and feedback loops keep the quality high
* **Courage**: Making the best choices for the project, even if it means throwing things away or doing a different approach
* **Respect**: Every team member is important and valuable

### XP Principles

* **Humanity**: Software is built by people, and the needs of those people need to be balanced with the needs of the project.
* **Economics**: Someone's paying for this, and someone needs to be mindful about the cost
* **Mutual Benefit**: Search for practices that benefit the individual, the team, and the customer together
* **Self-similarity**: The pattern of a monthly cycle is the same as weekly cycle is the same as a daily cycle.
* **Improvement**: Do your best today, know what you need to do to be better tomorrow
* **Diversity**: Lots of different opinions and perspectives make better products
* **Reflection**: Stay aware of what's working and what's not
* **Flow**: No distinct phases
* **Opportunity**: Each problem is a chance to learn something new about software development
* **Redundancy**: Redundancy can avoid big quality problems
* **Failure**: It's ok to try things that don't work
* **Quality**: You can't deliver faster by accepting a lower quality product
* **Accepted responsibility**: If someone is responsible for something, they have the authority to get it done
* **Baby steps**: Take small steps in the right direction

### Corollary Practices

* **Real customer involvement**: Bring customers to your meetings and listen to them
* **Incremental deployment**: Deploying small pieces of the system individually
* **Team Continuity**: Keep effective teams together
* **Shrinking Teams**: As a team becomes more effective, instead of adding more work, remove a team member and use that team member to bring XP culture to another team
* **Root-Cause Analysis**: When something goes wrong, figure out what the problem was, what caused it, and eliminate the problem upstream
* **Shared code**: Collective ownership
* **Code and tests**: Only the code and tests are maintained by the team. Documentation is generated automatically, and history is shared through word-of-mouth culture
* **Single codebase**: Don't manage multiple versions of the code
* **Daily deployment**: Push a new version of the software into production every day
* **Negotiated scope contract**: Instead of fixing scope and negotiating time, fix time and negotiate scope.
* **Pay per use**: Instead of charging for development, charge the customer when they use the system. This is real-time, constant feedback about which features are being used and which aren't.

### Bad XP Shortcuts

These are better than not doing anything, but don't capture the values of XP. The values matter, but they're less concrete than the practices, so they're harder to train. They also don't force the team to acknowledge that anything is wrong.

* Using code reviews instead of pairing.
* Having frequent meetings instead of sitting together.
* Don't have the team integrate, just do it on the server.
* Write the tests last.

The canary in the coalmine for XP falling apart is people not pairing.

### Differences from Scrum

* No fixed roles- a "PO" can also be a developer
* No retro, because you're never-not retroing
* Can be adopted more piecemeal

## XP, Simplicity, and Incremental Design

The larger goal of XP is to help teams build software that can be extended and changed easily.

Lack of simplicity: An all-in-one mixer/blender/processor. Instead of enabling a range of recipes to be made, it prevented them and prevented the problem from getting fixed because buying standalone tools feels redundant. It's worse than useless.

The waste generated by tracking time-on-task is huge- by trying to make sure everyone is 100% allocated, you burn 20% of the time tracking doing something that adds no value.

Design is deferred until the last responsible moment to take advantage of all possible information. This helps evolve the software design slowly and live with much simpler plans. You need to consistently and constantly refactor your code as a result. When teams are constantly refactoring, they also write code that is easier to change. The most damaging thing you can do to a codebase is writing bad code, then write more bad code that depends on it.

Integrating code sooner prevents you from building two parts independently that don't fit together. If the code relies on big plans, the team doesn't have any incentive to write modular code, and is more likely to run into an integration problem from following the plan for their monolith.

Increasing time pressure on a team encourages them to drop quality, which ends up making everything take longer.

### Code Smells

* **Shotgun surgery**: Changing code in one place requires it to be changed many others
* **Half-baked code**: Using one piece of code requires a bunch of other code to be initialized
* **Very large classes**: Doing more than one thing
* **Duplicated code**: Shows up in more than one place
* **Spaghetti code**: Tangled structure
* **Lasagna code**: Tangled layers
* **Hooks**: Adding hooks for intended future functionality (which is making decisions about how something will work before you have to)
* **Bulletproofing**: Handling every edge case

### The Framework Trap

Instead of solving the actual problem, solving the entire category of problems (YAGNI). Libraries are about splitting code up, frameworks are about bringing code together. Turning your code into a framework is making decisions for people in the future, and forcing them to think about their problem in a very specific way. Combining a lot of pieces doesn't save time, but they're actually limiting their ability to respond to new needs and information. Don't design for reuse- design for use, design for a second use, then refactor those shared behaviors into the resuable pattern. Let complex behaviors emerge from simple interactions, instead of deep command hierarchies.

> Me: "This framework will work for 5 years!"
> Me in 5 years: "Why am I stuck using 5 year old technology??"

### Holistic Practices

Can't be adopted piecemeal.

* **Incremental Design**: Make design decisions at the last responsible moment, and never stop designing
* **Energized work**: Give everyone enough time and freedom to do the work correctly
* **Whole Team**: Working together to overcome obstacles

### Kent Beck's Repsonse to DHH Regarding TDD

```
DHH has consigned TDD to the scrapheap of history. I'm sad, not because I rescued it from the scrapheap of history in the first place, but because now I need to hire new techniques to help me solve many of my problems during programming:

* Over-engineering. I have a tendency to "throw in" functionality I "know" I'm "going to need." Making one red test green (along with the list of future tests) helps me implement just enough. I need to find a new way to stay focused.
* API feedback. I need to find a new way to get quick feedback about my API decisions.
* Logic errors. I need to find a new way to catch those pesky sense-of-test errors I'm so prone to making.
* Documentation. I need to find a new way to communicate how I expect APIs to be used and record what I was thinking during development.
* Feeling overwhelmed. I'm really going to miss how, using TDD, even if I couldn't imagine an implementation I could almost always figure out how to write a test. I need to find a new way to take that next step up the mountain.
* Separate interface from implementation thinking. I have a tendency to pollute API design decisions with implementation speculation. I need to find a new way to separate the two levels of thinking while still providing rapid feedback between them.
* Agreement. I need to find a new way to be precise with a programming partner about what problem I'm solving.
* Anxiety. Perhaps what I'll miss most is the way TDD gives me an instantaneous "Is Everything Okay?" button.

I'm sure I'll find other ways to solve all these problems. In time. The pain will fade. Farewell TDD, old friend.
```

## Lean, Eliminating Waste, and Seeing The Whole

Lean is a mindset, rather than a collection of practices.

* "Multitasking" is a term people use when they mean "overloaded"
* "If stupid enters the room, you have a moral duty to shoot it, no matter who's escorting it."
* Pull systems eliminate constraints

### Measurements

* Lean teams use measurements to make sure that everyone is seeing the project and the way their actions impact it in the same way (like lead time).
* A WIP area chart can help see how quickly software is being delivered.
  * Track how many stories are in each stage of the process at once
  * A ribbon getting narrower means more flowed into the stage than out
  * You can notice trends when a lot of things move together
  * A solid line means a blockage

### Waste

Waste is anything that doesn't actively help you build better software. The project manager relentlessly updating plans, binders of specs, people reciting statuses to be copied by a PM into meeting notes no one will look at.

Seven software wastes:

* **Partially done work**
* **Extra processes**: eg. creating a lot of time estimates
* **Extra features**
* **Task switching**
* **Waiting**
* **Motion**: eg. not sitting together
* **Defects**

Every one of these is probably useful for someone, sometime. They are waste in terms of building valuable products.

### Value Stream Mapping

Map the steps it takes to deliver a minimally marketable feature. The line goes up when it's being worked on, and down while waiting for the next step. For example:

* Create requirements document (4 days)
* 8 days
* Task breakdown and estimation (6 days)
* 4 days
* Create project schedule (3 days)
* 5 days
* Review plan and get approval (1 day)
* 6 days
* Develop software (12 days)
* 1/2 day
* Test software (8 days)
* 3 days
* Validate scope is complete (1/2 day)
* 9 days
* Deploy (1 day)

In this, it was 71 days from the time the team started working to when it was deployed. Of this, 35.5 were spent waiting.

### Integrity

* Perceived integrity: How well a product meets the needs of the person using it
* Conceptual integrity: How well the features form a single, unified product

### Options thinking

What do you have the option (but not the obligation) to do?

* In scrum, the team is committed to delivering valuable software at the end of a sprint. They have the option to do that by delivering specific features, but that can change if the PO pulls them out or if they can't be done-done.
* There are no "late tasks"- the team can always change the tasks if it helps them develop valuable software
* Designs are options, not commitments- if you find a better way to do something (a better option), you should take it
* Decoupled components give you lots of options

### Set-based development

Have the team follow several paths simultaneously to build alternatives you can compare. You can frequently check-in to see which approach is appearing more promising. This can save tons of time speculating.

### Heroes and Magical Thinking

Believing that if you set high goals and tight timelines, people will rise to the occasion inevitably creates a hero culture of individuals rather than a cohesive team. The manager thinks their team is magical, and they can pile anything on them and it will get done. No one looks too closely at the quality of what's being built, how many stop-gaps are being thrown in, or what's being done to the team dynamic. All that's recognized is the number of hours, so that's what people start giving. Working a lot of hours results in slower delivery, not faster.

Lean is a mindset for making how the team works more explicit.

### Lean Values

* **Eliminate Waste**: Find work you're doing that doesn't directly help create valuable software and eliminate it
* **Amplify Learning**: Use feedback to improve how you build software
* **Decide as late as possible**: Make every important decision for your project when you have the most information about it: the last responsible moment.
* **Deliver as fast as possible**: Understand the cost of delay, and minimize it with pull systems and queues.
* **Empower the team**: Establish a focused and effective work environment, and build a whole team of energized people
* **Build integrity in**: Build software that intuitively makes sense to users and which forms a coherent whole
* **See the whole**: Understand the work that happens on your project, and use the right kind of measurements to make sure you're actually seeing everything clearly.

## Kanban, Flow, and Constantly Improving



## The Agile Coach

* Talk to team members separately and try to understand how their perspectives differ across the different roles.
  * Ask them what they think about each of the values and principles
  * Find out what frustrates them, what motivates them, and what drives the decisions they make
  * Find out which agile principles affect them the most (positively or negatively)
* Find the agile practices the team thinks feel "empty" and are giving them better-than-not-doing-it results
* Look for values or principles they're already tacitly aligned on
* Help the team understand that working long hours leads to less code (not more), and the quality is lower too
* Identify the person with the authority and willingness to be a product owner early- they need to have buy-in from the business
* If a team is just doing a daily status meeting, help them learn the difference between self-organization and command-and-control
* Let the team fail. Don't let them drive off a cliff, but use the dozens of opportunities that naturally come up during sprints. Teams that fail and recover together are stronger and faster than ones that are protected. The team may also surprise you by being right.
* Understanding collective commitment is really hard. Look for places where team members are hesitant to estimate or try to get out of planning.
* Find team members who have "tunnel vision" about a particular feature, and get them exposure to other features to help make their view more holistic.
* Make sure all the data (burndown, backlog, etc) is in a visible area
* You won't solve the politics of a company; focus on helping the team see what the politics are first.
* Some cultural changes are big enough that adopting them could get everyone involved fired
* Help the team find examples where they were hesitant to show something to someone outside the team. Have they ever manipulated a demo to work around a bug?
* Help the team create information radiators.
* Does the team fall into the framework trap?
* Help them find examples of code that was never needed, features that were never used, and sometimes never requested.
* Rather than engage in a debate, try to uncover what specific problems the team is having with practices like pairing or TDD. Coach them through executing the practice.
* Don't let an enthusiastic team member make a practice seem like zealotry
* What kinds of waste does the team have?
* Gently work with managers to recognize their own magical thinking- don't create friction between the team and the company
* Separate the idea of the process from the people working on it

### Barriers to Scrum

If the organization will do scrum practices but not embrace scrum values, they'll get better-than-not-doing it results (but it's not scrum). Don't overpromise the transformation.

Managers and executives spending time with the team is a big barrier to adoption, as is dedicating a product manager to being embedded in the team. They have to have to value the software that's being built enough. It's also very expensive to have a phalanx of BAs and managers to prepare all the documentation for the executives to read.

Is the team and the boss OK with:

#### Commitment

* Relinquishing control of the project to the team
* Not going off on their own to build something and trying to integrate it at the end
* Not having a single wringable neck
* Listening to comments and feedback even if you disagree with them
* Actually being willing to take responsibility? Everyone on the team?

#### Respect

* Trusting the team to do the right thing and deliver as early as possible, even if that means being late?
* Giving the team enough time
* Trusting the team to choose the right tasks for the right people
* Not being able to say you don't know why the team did something they did

#### Focus

* Never asking someone on the team to do something that's not part of the current sprint
* Never asking someone on the team to do work that the whole team hasn't agreed on
* Putting what's most valuable to the company ahead of other concerns
* Not demanding that tasks be done in a particular order up front

#### Openness

* Listening to what others say and thinking about it
* Thinking about users and project planning, even if you never have before
* Thinking about technical details, even if you never have before
* Thinking about what the person next to you is doing and whether it fits into the overall goal
* The person next to you thinking the same thing about you

#### Courage

* Not being able to blame lack of planning on the project manager
* Not being able to to poor requirements on the PO or senior manager
* Taking the time to really understand your users
* Building something that isn't perfect because what your users really need is good enough
