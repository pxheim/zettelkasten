Martin, R. C. (2021). _Clean craftsmanship: Disciplines, standards, and ethics_. Prentice Hall.

[[$Bibliography]]

A discipline will consist of an essential part and an arbitrary part, both of which are required. The essential part is the main idea behind the discipline, whereas the arbitrary part gives it some substance.

E.g. good code should consist of at least 80% unit tests. The essence is that you need to test your code to ensure that it works, the arbitrary part is 80%.

When disagreeing with a discipline, make sure that you don't just disagree with the arbitrary part.

[[software-craftsmanship]]

# TDD

[[test-driven-development]]

[[3a-pattern-for-tests-arrange-act-assert]]

[[boy-scout-rule]]

[[refactoring-should-never-be-planned]]

[[mezaro-test-doubles-vocabulary]]

[[be-bad-at-the-tools-you-should-not-use]]

[[decouple-tests-from-file-layout]]

[[keep-tests-specific-to-single-class]]

[[specific-tests-make-for-generic-code]]

Every test you write is a transition in the finite state machine that you are trying to create in your program. Your program is a finite state machine as your computer is a finite state machine processor. How do you ensure that all transition changes are tested? Well, by writing tests first!

# Refactoring

[[refactoring]]

[[extract-functions-until-you-no-longer-can]]

[[give-good-names-to-your-functions]]

[[extract-variables-wherever-you-can]]

# Simple Design

[[simple-design]]

[[yagni-you-arent-gonna-need-it]]

How much coverage is enough? 100%, that's the only way you know that all your code actually works, but it's unreachable in most cases. Still, aim towards it as an asymptotic goal.

Testable code facilitates simple design as you need to write good code for it to be testable.

There are two types of duplication, real duplication and accidental duplication. Real duplication is bad, and should be removed. Accidental duplication is duplication where it's often the intention that the duplicated code either represents different things, or will evolve in different directions.

After doing the green, red, refactor loop to get where you want, the last step is often to clean up everything (a last refactor if you will) where you make the code as small as possible without making it less expressive.

# Collaborative programming

[[collaborative-programming]]

# Acceptance tests

[[acceptance-tests]]

# Productivity

> Ask GPT to be my new CTO?

[[never-ship-shit]]

When asked to change something, developers should come up with an estimate that is proportional to the scope of the change. Making software that is inflexible goes against the whole point of making software. Alas, this is often the case due to missing testing and refactoring.

The rhythm of releasing software should be quick. At most a week or so. At best software should always be ready to be released. This is possible through good tests and communication.

Stable productivity is only possible if testing discipline is kept from the start. Otherwise productivity will decline until a complete rewrite is in order.

# Quality

[[qa-should-be-at-the-front]]

# Courage

[[your-responsibility-that-bus-factor-is-not-1]]

Give honest estimates.

Say no. Managers need it.

[[learn-one-new-language-every-year]]

Mentor people. Always. The best way to learn is to teach.

# Ethics

[[oath-of-the-programmer]]

# Harm

[[poor-code-leads-to-harm]]

[[rushing-often-comes-from-within]]

Good structure comes from writing tests first. You cannot test code with poor structure.

Code with poor structure is
- Rigid: Minor changes to the system is hard to integrate with the rest of the system
- Fragile: Minor changes force many changes in other modules. Then, that small change is likely to cause something else to break.
- Immobile: If you want to use some part of code and you cannot because it's so entangled in other code.

Structure is more important than behavior, but this contradicts "make it work and then make it right.". This is why when working on user stories, you first make it work and then you do not ever move on until you have the structure right. TDD follows this.

Structured programming, proven by Dijkstra that any computer program can be broken down into only 
- Sequence: lines of code in order.
- Selection: if, else, switch, etc.
- Iteration: for, while, etc.

As a result of structured programming came functional decomposition, the act of starting your program at the top and breaking it down into smaller and smaller functions that are ultimately testable.

# Integrity

Following the story of version control, in the start the cycle time was the length of the project. Then gradually, as new tech became available, the cycle time shortened more and more until we got to where we are today, CI.

[[branching-is-bad-for-ci]]

If, after your tests pass, you are confident that you can deploy to production, your tests are good enough. Otherwise they are not.

CD does not mean that you _should_ deploy multiple times per day, but instead that you _can_ deploy multiple times per day. As a developer you should always be ready, and when business comes, you can tell them to go ahead.

Never allow the build to fail.

[[code-coverage]]

[[mutation-testing]]

The goal of test coverage and mutation testing is to create a test suite that ensures semantic stability, i.e. it tests that the system does what it's required to do.

[[boy-scout-rule]]

The only way to go "fast" as a developer is to go "well". Do the right thing. Do TDD. Refactor. User proper design patterns. Clean code. These are all indirect ways of going fast.

Three direct ways of achieving productivity:
- Viscosity: How long does it take you to do things. Coding is only a small part of being a developer. Make sure things like building, testing, debugging and deployment all are super fast.
- Distractions: Meetings should only be attended when you are needed. Otherwise leave. Subjective: Try to code without music. It occupies the brain. Also, try to resist getting into the flow. The code produced then seems to be quite bad.
- Time management: Pomodoro timer. Divide work into segments of 25 minutes then 5 min break. Do not let yourself get interrupted during those 25 minutes. If someone needs you, get back to them during your 5 minutes.

# Teamwork

If working remotely, create a virtual team room where everyone is at the same time. Mic active most of the time. Create the illusion of a shared office.

Work at least 6 hours in the same room.

Get together at least one week per quarter.

Estimates based on an end date is a lie. Even if you _need_ to make a deadline, it just encourages lying about the estimate to ensure you meet the deadline.

[[when-estimating-a-task-add-fudge-factor]]
