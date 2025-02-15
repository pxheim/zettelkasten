
[[$Bibliography]]

Kaicen - Japanese word for "small improvement". Used in the way where small improvements to yourself every day is a pathway to success.

Don't make excuses, instead provide options when something cannot be done. Dont be afraid to say that you don't know, but make sure to follow up with "but I'll find out".

Fix the "Broken Windows" in your code, i.e. the bad parts that smell. Research shows that broken windows in your code will make the rest deteriorate as well.

Introducing change in an unwilling org. can be done by giving them a taste of the change first, e.g. what you can do on your own and then go "it would be even better if we had...".

Know when software is good enough. Don't add all the bells and whistles unless you know you're going to need them. Most likely YAGNI.

Treat your knowledge like an investment portfolio.
- Invest regularly: make a habit of learning. Pref. fixed time and place.
- Diversify: Don't get stuck with one tech.
- Manage risk: Don't bet on just fancy new tech.
- Buy low, sell high: Might be risky to learn new tech, but might be worth it.
- Review and Rebalance: Tech you might have dismissed before might be relevant now.

Some goals to keep you motivated:
- Read 1 technical book per month.
- Read 1 non-technical book per month (soft skills).
- Learn 1 new language per year.
- Whenever you answer "I don't know", take it as a challenge to find out.

Communication is probably the second most important skill for any developer.

Always make code easier to changes. This cna often explain why we do all the things we do, to make things etc.

DRY is not meant to literally mean don't have to instances of the same code in two places, but instead means don't have the same knowledge or intent in multiple places. If making on change, how many places tdo you have to change code?

Duplications of code is OK if intent is different.

Documentation (comments) can also be a source of code duplication. The comments explaining exactly what the code does is vilolating DRY.  (see note on refactoring).

Data models must also be DRY! If two properties can be used to calculate a third, this third variable should be just that.

Orthogonal components are components that are not coupled. This provides a plethora of benefits such as increased productivity as you don't have to change them when done, promotes reuse as they can be combined and increased productivity as there's no overlap in functionality.

Write "shy" code, i.e. code that does not reveal anything to other modules and that does not rely on other module's implementation.

Code decoupling can be seen when writing tests. If it's easy, code is most often well structured and decoupled. Same if fixing bugs is easy.

Code as if whatever tech, library or whatever you use might change. Make it ETC.

Tracer-code is code you write to quikcly get something out to your customer in order to get feedback. It's not a POC as it's not meant to be thrown away, and it's not a prototype for the same reason. Tracer-code is made the way you would make production code, but aims at finishing some feature that touches the whole stack fast.

Change unit of estimation as time goes up, e.g. avoid something like 130 days and instead estimate it to take 6 months.

Avoid giving estimates you don't know with some degree of certainty. Instead say "I'll get back to you".

---

IT does not mater whose bug it is, it's still your problem, so fix it, don't blame.

When debugging, always write a failing test.

The OS is probably not broken, nor is the lib or hosting provider. It's your code.
 
If fixing a bug takes a long time, ask why. Is there anything you can do to catch the bug earlier? Try to crash early.

Keep an engineering daybook where you jot down stuff you come across on a daily basis as well as what you do every day. When full, write teh day on the spine and start a new one.

---

DBC, design by contract, is a design tool to help you write better code. Consider pre and post conditions of anything you write. Pre-conditions can often be caught with asserts.

Crash or fail ASAP. Sometimes adding a ton of error handling in terms of try/catch can make things worse, more coupled, less redable.

Use assertion! But do not have it replace proper error handling.

Each method should finish what they start. A method should not open a file, only to have it be closed in another method. This also applies to classes. We have constructors and destructors.

Take small steps! This way you can ensure feedback on the changes you make and you avoid "outrunning your headlights", or trying to predict the future.

Always "tell, don't ask", basically don't expose information from otherclasses in method calls. Instead of `customer.orders.find(order_id)` do `customer.findOrder(order_id)`. This way, customer does not have to care about how to find an order.

Global data is the root of all evil when it comes to coupling. Wrapping global data in a singleton is cheating. Any mutable global (or external) resource is bad. Wrap it in code you control.

Inheritance is bad and you should never use it. It introduces coupling that can be hard to break, and worse, can have multiple instances of inheritance. A class w/o 20 methods that's inherited still expose those 20 methods even if only 2 are actually used.

Alternatives to inheritance:
- Interfaces & protocols: e.g. Car implements Drivable and Locatable where the latter is an interface w/o code. For Drivable they just say that whoever implements it must also implement getSpeed() and stop().
- Delegation [[$Research]]
- Mixins [[$Research]]

Move all configurations to an external API.
- Credentials for services (APIs, etc).
- Logging levels and destinations.
- Port, IP, etc.
- Env. specific validation params.
- Externally set params, e.g. tax rate.
- Site specific formatting details.
- License keys.

Temporal coupling is when some part of code have to happen before another. They are coupled by time. Make activity diagrams to visualize temporal coupling. Probably amazing to do for app startup sequence.

Share state is bad / incorrect state. Use semaphores to protect a resource when multiple parts of your code can access it at the same time.

Concurrency is hard to get right so unless you strictly need it, don't.

Actors make concurrency easier. An actor is a piece of code with its own local and private state and a mailbox. When an actor gets mail, it does something and then goes back to sleep.

Listen to your lizard brain (insticts). The are all your years worth of knowledge trying to tell you something.

If coding feels like walking uphill in mud, go do something else for a whle, and come back to the problem. You're likely on the wrong path.

Avoid coding by coincidence. Code deliberately, meaning don't make assumptions, don't guess why things work, don't code in the dark and document your assumptions.

Consider the BigO notation for your algorithms. You don't have to go crazy, but know that simple loops are O(n) and loops in loops are O(n2) or more. Reduce n2 by divide and conquer or other techniques.

Remember that we are terrible at optimizing code so make you you optimize only when needed.

If you cannot refactor something quick and it takes a week, it's not a refactor. It should then be planned and estimated.

Never refactor and add functionality at the same time.

The biggest benefit of testing comes from how you think when having to write them. Argues that since this is true, you can forgo testing if you have done it long enough. What about refactoring then?

Pitfalls of TDD: You get distracted by 100% test coverage, you end up with poor and redundant tests and you'll end up writing things from bottom up vs e2e, which is preferred.

Property testing tests contracts and invariants:
- Contracts: input x should generate output y.
- Invariants: things that should always be true, even after state has been through your function, e.g. length of list should be the same after sorting.

These tests then run on random sets of data. Hopefully they'll pass.

When naming functions, try to give a name indicating why it does what it does. E.g. deductPercent states what is done, but applyDiscount is clearer.

Don't break the clture of the language you are writing in, e.g. i, j,k might be common to use in loops, so do that.

Noone knows exactly what they want. Your job as a developers is to figure out together with the client what exactly they want. Talk to the client. This is requirements gathering.

Become the client. Work as a client would for a day or two to get a feel for what they want / need.

Requirement documents are not for the clients to see. Instead use index cards for them or when interacting with them.

Maintain a glossary with the client to ensure you're talking about the same thing.

How to apply agility at everyday tasks?

- Work out where you are
- Make the smallest change possible towards where you want to be.
- Evaluate where you ended up. Fix anything you broke. Go back to 1.

---

Don't adopt new tech or new methodologies just because it's the next cool thing or because some wildly successful company is doing it. Do what works for you. There's no "one size fits all".

VCS should control build, test & deployment via commits or pushes. Sagging or prod should happen via tagging.

Delight your customers or clients. Talk to them, figure out their problems, and solve them. You're not a coding monkey, you're a problem solver.

Be proud of your work, proud enough to sign it publicly.

---

