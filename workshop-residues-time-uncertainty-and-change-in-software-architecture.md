O'Reilly, B. (2024, June 10). _Residues: Time, change, and uncertainty in software architecture_ [Workshop].

Residuality theory. Scientific theory of how we can do architecture. Peer reviewed.

How do you make design decisions?
- Collect information from stakeholders?
- Identify constrains rel. to project.
- Evaluate pros and cons of varying solutions. Which one fits the bill for the project in question.

Gut feeling is the root of most decisions when it comes to coding and architecture. However, gut feeling is not "random". Your gut feeling is the years of experience telling you subconsciously what's the right path.

Standard ways of represent architecture (UML, etc.) does not have way to factor in time, change, over time and uncertainty of change.

How do you deal with time, change and uncertainty:
- Small services.
- Don't worry about it? (most commonly)
- Grouping by business logic.
- Agile (everything is going to change, so let's not worry about it)

You don't get to control time, change and uncertainty. You need to deal with it and work around it.

What is your unit of software architecture? It depends on what "level" you are on. Business might have "features" as their unit, whereas a developer will think about "services". Design and developers do the same thing. You cannot take a design and break it down into services without some form of mapping.

Proposed new unit for software engineering is **residue**.

Everyone is doing architecture differently as we've all learned it from different places. We are all formed by the path we go through in our carreers.

[[book-schon-the-reflective-practitioner]]

Architecture is not a structured practice. It's basically faking it, but pretending to know what you are doing. David Parnas mentioned this in his paper on how to fake it.

When considering tools for architecture, none of them can be considered required as successful IT projects all use a different variation of them. Thus none of them are required. What's actually making them successful must therefore be something else.

The tools applied are there to "do the walk" many many times looking at the problem from different angles.

Data models are the bane of architectures E.g. defining a customer w/ ssid and credit card. Business changes and you now have to deal with business customers and your model breaks. Creating weak abstractions therefore are bad.

Viewing the world in terms of defining things is what we do, and therefore also how we make software.

---

Software is ordered, meaning that it's predictable. If you give it an input, you know what output to expect. Businesses are disordered, meaning there's no pattern and things are random. Architecture is hard because we have to make something ordered (software) in a disordered environment (business)

---

Complex systems have non-linear responses to inputs, are coupled, unpredictavle emergent behaviors.

Complexity science is the study of complex systems.

5 ways of describing complexity.

1. Cynefin (pron. "knevin"): divides into 5 domains:
	1. Obvious: Things are 
	2. Complicated: not obvious how to solve problem, but can do wit from experience. Ordered.
	3. Chaotic: "Tiger runs into the room"
	4. Complex: Do small experiments. figure out.
	5. Confused: ?? You don't know, you apply the wrong domain to your problem.

Constraints. Example. cars driving on a road. The line separating which side to drive on is a constraint. Thus, we move from a chaotic env to a complex one. Now what about junctions? We add another constraint to make the system less complex. Then we add more constraints until we get to a system that's complicated. You then get some auth to make you take a test to prove that you can drive and get into the obvious domain.

More and more constraints enable you to move from chaos --> complex --> complicated --> obvious.

2. Complex responsive process

Focus on the process, not the thing. Book.

3. Antifragility

A system that comes back stronger than before when presented with a black swan event.

Things are random. We are fooled by it all the time.

Black swan effect, the things that are most unlikely tend to define how we do something, e.g. systems engineering. Same as "what if we lose Italy". As an architect, you should identify and ignore them.

80/20 rule. The stuff we expect to happen are the 80%, the rest are 20. But if drawn as a power curve, the probability of a 20% even happening is 1. How do we deal with these issues that are definitely going to happen?

- Ignore them?
- Heuristics. Thing we have learned that are hard to unlearn. Dangerous for software dev as it's hard to change.

Stress is they key to building a system that is anti-fragile.