Martin, R. C. (2019). _Clean Agile: Back to basics_. Prentice Hall.

[[$Bibliography]]

Because the simple and small message of Agile has become muddled over the intervening years. It’s been mixed with the concepts of Lean, Kanban, LeSS, SAFe, Modern, Skilled, and so many others. These other ideas are not bad, but they are not the original Agile message

*****

[[four-values-of-agile-development]]

[[iron-cross-of-project-management]]

[[agile-provides-data-to-make-the-right-decision]]

[[agile-development]]

the thing about implementation is that is actually has to be done. Analysis and design are not binary deliverables. They do not have unambiguous completion criteria.

*****

I call this Runaway Process Inflation. We’re going to do the thing that didn’t work, and do a lot more of it.

*****

Iteration Zero is also used to set up the development environment, estimate the stories, and lay out the initial plan.

*****

This process of writing stories, estimating them, planning them, and designing never stops.

*****

At the end of the iteration, some fraction of the stories that we had planned to finish will be done. This gives us our first measurement of how much can be completed in an iteration. This is real data. If we assume that every iteration will be similar, then we can use that data to adjust our original plan and calculate a new end date for the project

*****

This loss of hope is a major goal of Agile. We practice Agile in order to destroy hope before that hope can kill the project.

*****

Agile is about knowing, as early as possible, just how screwed we are.

*****

Managing the Iron Cross

> Change schedule, good.
> Hire people, bad.
> Code "faster", bad
> Change scope, good.

*****

Actually, this is exactly the opposite of the case. Brooks’ law states: Adding manpower to a late project makes it later.

*****

Agile. Circle of Life

> Make a note about all the aspects of the circle of life.

*****

Virtually all other Agile processes are a subset of or a variation on XP.

*****

Agile development is important for much deeper philosophical and ethical reasons. Those reasons have to do with professionalism and the reasonable expectations of our customers.

*****

Another source of artificial delays is the notion of stabilization. Teams will frequently set aside a period of continuous testing during which they watch the system to see if it fails. If no failures are detected after X days, the developers feel safe to recommend the system for deployment.

> This also goes against CI. Build should be working until proven otherwise.

*****

When the business sees a feature work, they expect that feature is done.

*****

But who is training the new people? The people who made the mess in the first place.

*****

If a change to the requirements breaks your architecture, then your architecture sucks.

*****

The older a software system is, the better it should be.

*****

QA should wonder why they are stuck at the back end of the process checking systems that always work.

*****

For example, you may not know how long something will take, but you can compare one task to another in relative terms. You may not know how long it will take to build the Login page, but you might be able to tell me that the Change Password page will take about half the time as Login.

*****

As CTO, I expect you to keep learning.

*****

As CTO I expect you to teach.

*****

Agile was to heal the divide between business and development

> Note on the Bill of Rights

*****

In short, we cannot agree to deliver fixed scopes on hard dates. Either the scopes or the dates must be soft.

*****

An estimate is a guess; we want some idea of how long the project will take without actually building the project.

*****

One technique that works quite well for large tasks is trivariate estimation. Such estimates are composed of three numbers: best-case, nominal-case, and worst-case

*****

research the program evaluation and review technique (PERT).

*****

Typically, we write the story on an index card.

*****

It turns out that being able to hold those cards in your hands, pass them across a table to each other, scribble on them, and otherwise handle them is immensely valuable

*****

What makes a story manageable, schedulable, and estimable is the temporary lack of detail. Stories must start out cheap because a lot of them are going to be modified, split, merged, or even discarded. Just keep reminding yourself that they are placeholders, not requirements

*****

Login is now our Golden Story.

*****

Why 1 to 6? Why not? There are many schemes for assigning cost. The simpler ones are usually better.

*****

But there is a beautiful thing about vague and fuzzy numbers. It’s called the Law of Large Numbers.4 When taken in quantity, the fuzziness integrates out!

*****

Meanwhile, it’s time to plan the first iteration. The iteration begins with the Iteration Planning Meeting (IPM). This meeting should be scheduled to be one-twentieth the duration of the iteration. The IPM for a two-week iteration should require about a half a day.

*****

The whole team attends the IPM

*****

how many story points the programmers think they can complete. This number is called the velocity.

*****

The four-quadrant game
The stories that are valuable but cheap will be done right away. Those that are valuable but expensive will be done later. Those that are neither valuable nor expensive might get done one day. Those that are not valuable but are expensive will never be done.

*****

And on it goes like this.

> Guess at velocity, say 30
> Check at midpoint. Multiply this by 2 and then compare with velocity. Add or remove tasks as necessary. If mid is 11, we assume that by end of iteration we can get 2x11 done, so remove 8 points.
> Check at end of iteration.
> Next week's point goal will be whatever the end of last iteration was.

*****

User stories are simple statements that we use as reminders of features.

*****

Stories follow a simple set of guidelines that we remember with the acronym INVEST

*****

Refactoring is never a story. Architecture is never a story. Code cleanup is never a story. A story is always something that the business values.

*****

Flying Fingers

*****

Planning Poker6

*****

So splitting is almost always possible. The challenge is maintaining INVEST.

*****

A spike is a meta-story, or rather, a story for estimating a story

*****

It is far better to get 80% of the stories done than it is to get each story 80% done

*****

Managers and leads will be tempted to assign stories to programmers. This should be avoided.

*****

If QA has not already begun to write the automated acceptance tests, they should start as soon as the IPM ends.

*****

We expect them to all be written before the midpoint of the iteration. If not all the acceptance tests are ready by the midpoint, then some of the developers should stop working on stories and start working on acceptance tests.

*****

The demo should include showing that all the acceptance tests run—including all previous acceptance tests—and all unit tests.

*****

If we see a positive slope, it likely does not mean that the team is actually going faster. Rather, it probably means that the project manager is putting pressure on the team to go faster.

*****

If the velocity chart shows a consistent negative slope, then the most likely cause is the quality of the code. The team is likely not refactoring enough and they are probably allowing the code to rot

*****

One way to avoid inflation is to constantly compare story estimates back to the original Golden Story

*****

break the coupling between release and deployment. The term “release” means that the software is technically ready to be deployed. The decision to deploy becomes solely a business decision

*****

The business writes formal tests describing the behavior of each user story, and developers automate those tests.

> The flow of acceptance tests

*****

Rather than acting as testers on the back end of the project, they become specifiers operating at the front end of the project.

*****

Moving QA to the beginning and automating the tests solves another huge problem. When QA operates manually at the end, they are the bottleneck

*****

It is the programmers’ job to make sure that their code passes all the tests. So of course, the programmers must run those tests.

*****

Notice that this practice is counted as a business practice, and not a team practice. That’s because the primary advantages of the Whole Team practice accrue to the business.
When teams are co-located, the business runs much more smoothly

*****

I’ve heard that it is possible. I’ve never seen it done successfully. Perhaps you have.

> Agile teams cannot work unless they are in the same office?

*****

a team composed of people who work almost entirely from home will never work as well as a team that is co-located.

*****

A metaphor can provide a vocabulary that allows the team to communicate efficiently. On the other hand, some metaphors are silly to the point of being offensive to the customer.

> A way to talk about your software through metaphors.

*****

Ubiquitous Language, which is the name that should have been given to the Metaphor

*****

What the team needs is a model of the problem domain, which is described by a vocabulary that everyone agrees on. And I mean everyone—the programmers, QA, managers, customers, users…everyone.

> This replaces the metaphor.

*****

That was the moment that I learned that a software project is a marathon, not a sprint, nor a sequence of sprints.

> Steady progress is most important 

*****

This is not to say that all overtime is bad, nor that you should never work overtime. There are extenuating circumstances for which the only option is to work overtime.

> Overtime is almost always bad. Means you, or someone in your team, is a bad planner. There are certain times overtime is OK, bit they are extremely rare.

*****

My rule of thumb is that the first hour of insufficient sleep costs me two hours of daytime work. The second hour of insufficient sleep costs me another four hours of productive work.

*****

The code is owned by the team as a whole. Any member of the team can check out and improve any module in the project at any time. The team owns the code collectively

*****

spread rather than concentrate that experience.

*****

Maintain your ability to work outside of your specialty.

*****

And then a miracle happened. The pair partner that he had rejected went after him to talk him down. The other two pairs reprioritized their work, finished the merge, and got the project back on track. Thirty minutes later the student, now much calmer, came back in the room, apologized, and resumed his work—including pairing. He subsequently became an enthusiastic advocate for Agile development.

> This is Agile. Not just CI, but how the team handled the person leaving.

*****

The continuous build should never break

*****

There have been teams who, under the pressure of a deadline, have allowed the continuous build to remain in a failed state. This is a suicidal move.

> Never cheat the build

*****

The following are true of the Standup Meeting:
This meeting is optional. Many teams get by just fine without one.
It can be less often than daily. Pick the schedule that makes sense to you.
It should take ∼10 minutes, even for large teams.
This meeting follows a simple formula.

*****

What did I do since the last meeting?
What will I do until the next meeting?
What is in my way?
That’s all.

*****

Double-Entry Bookkeeping

> This is TDD for accountants. It is written in law that they have to do this. Why is it not so about TDD for programmers?

*****

Test coverage is a team metric, not a management metric. Managers are unlikely to know what the metric actually means. Managers should not use this metric as a goal or a target. The team should use it solely to inform their testing strategy.

*****

Do not fail the build based on insuffi cient coverage. If you do this, then the programmers will be forced to remove enough assertions from their tests in order to get the coverage numbers high enough.

*****

Kent Beck named the four values of Agile long ago. They are courage, communication, feedback, and simplicity.

*****

They realize that the best way to manage a software project over the long term is with a certain degree of aggression.
There is a difference between courage and recklessness.

*****

The belief that quality and discipline increase speed is a courageous belief because it will constantly be challenged by powerful but naive folks who are in a hurry.

*****

The strongest advice I can give you, however, is to adopt the full Circle of Life, including, and most especially, the technical practices.

> Whichever version of agile you pick, you must at least do this.

*****

What I have seen is the transition of teams and individuals, because teams and individuals are often directed by values that are aligned with Agile.

> Orgs often cannot transition to agile. Agile only works when the whole org is on board. Agile in a team can fake it if upper management does not want agile. Split into new agile company if parent company does not conform with agile values.

*****

Neither the managers nor the customers know who the coach is, nor even whether there currently is a coach.

> Agile coach should ensure that agile methodologies are followed even during stressful times.

*****

Nowadays, it is all too frequent that we see Scrum Masters who are not coaches at all but are simply project managers doing what project managers always did.

*****

Again, there’s often nothing wrong with the training programs that go along with these certifications. However, it is foolish to train just one special person. Every member of an Agile team needs to understand the values and techniques of Agile. Therefore, if one member of the team is trained, all members of the team should be trained.

> Certs are BS. Do not mean that the person will do a good job. Just means that they paid for the course.

*****

Agile is about software. In particular, it is about small software teams. I am always frustrated when people ask me how to apply Agile to hardware, construction, or some other task. My answer has always been that I don’t know, because Agile is about software.

> With focus here on small teams. Some 4-12 is a good number.

*****

Mikado Method6 and TCR (Test && Commit || Revert)7

> Research 

*****

Once you own a tool, the path of least resistance is to do whatever the tool provides regardless of whether it meets the team’s needs

> If you have a hammer, everything is a nail.

*****

investment

> Cautionary tale on using tools like Jira, asana, etc. They often take away from agile. Perhaps each team can implement their own tool as they see fit? No tool might often be needed. Just sticky notes or simple Trello might suffice.

*****

Agile Hangover.

> When trying to add agile, but failing at it. Mostly because managers want quick results and do not see the need for the other things like TDD and refactoring as part of agile.

*****

Agile coaches try to guide managers and delivery teams through the Agile processes, there is no one helping developers learn Agile technical practices and engineering.

> "fixing the process will fix the engineering". Not true.

*****

They need strategic thinking.

> Change from coding monkey to actual developer.

*****

Most modern Agile coaches do not have enough (if any) technical skills to coach developers on technical practices

*****

Companies are still not mature enough to understand that technical problems are in fact business problems.

*****

As aspiring Software Craftsmen, we are raising the bar of professional software development by practicing it and helping others learn the craft. Through this work we have come to value:
Not only working software, but also well-crafted software
Not only responding to change, but also steadily adding value
Not only individuals and interactions, but also a community of professionals
Not only customer collaboration, but also productive partnerships
That is, in pursuit of the items on the left we have found the items on the right to be indispensable.

> Software Craftsmanship manifesto

*****

The obsessive focus on a methodology or set of practices distracts teams and organizations from their real goals. The goal is to teach a child to ride a bicycle, not to adopt the training wheels

*****

Good practices are good until we discover better ones to replace them.

*****

since its creation in 2008, the Software Craftsmanship community considers XP the best set of Agile development practices currently available.

*****

TDD, Refactoring, Simple Design, Continuous Integration, and Pair Programming are heavily advocated by the Software Craftsmanship community—but they are XP practices, not Craftsmanship practices.

*****

Craftsmanship is not only about technical practices, engineering, and self-improvement. It is also about professionalism and enabling clients to achieve their business goals.

*****

Agreeing first on the goals to be achieved is essential when discussing practices. The only thing that should not be acceptable is to reject a practice without providing a better alternative.

*****

Developers should not ask authorization for writing tests. They should not have separate tasks for unit tests or refactoring

> They are not optional

*****

Conversations between developers and business should be about why, what, and when—not how.

*****

Combining Agile and Craftsmanship is the perfect way to achieve that.

> They are essential the same thing, but one from business perspective, and the other from a technical perspective.
