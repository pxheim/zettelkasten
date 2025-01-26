
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

