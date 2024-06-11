O'Reilly, B. (2024, June 10). _Residues: Time, change, and uncertainty in software architecture_ [Workshop].

Residuality theory. Scientific theory of how we can do architecture. Peer reviewed.

How do you make design decisions?
- Collect information from stakeholders?
- Identify constrains rel. to project.
- Evaluate pros and cons of varying solutions. Which one fits the bill for the project in question.

[[gut-feeling-is-experience-subconsciously]]

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

Data models are the bane of architectures E.g. defining a customer w/ ssid and credit card. Business changes and you now have to deal with business customers and your model breaks. Creating weak abstractions therefore is bad.

Viewing the world in terms of defining things is what we do, and therefore also how we make software.

---

Software is ordered, meaning that it's predictable. If you give it an input, you know what output to expect. Businesses are disordered, meaning there's no pattern and things are random. Architecture is hard because we have to make something ordered (software) in a disordered environment (business)

---

Complex systems have non-linear responses to inputs, are coupled, unpredictavle emergent behaviors.

Complexity science is the study of complex systems.

5 ways of describing complexity.

[[cynefin-framework]]

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

4 types
- fragile - breaks.
- ?? hard to break
- resilient - comes back the same.
- antifragile - comes back stronger.

Stress is they key to building a system that is anti-fragile. Use stress as a driver of design decisions. Not patterns, not risk, nothing else. Just stress.

Don't predict. Instead identify what you are sensitive to. Easier to figure out how you are going to break something instead of what is going to break it.

4. Hyperlimilaity

Ordered systems inside disorganized systems.

---

Watch the video about residuality. [[$Research]]

Kauffman Networks (RBN). Grid of boolean values. Button press will turn them randomly to 1 or 0. Extreme amount of patterns. Change functionality so that each value can communicate with neighboring values. Reduces the amount of patterns drastically. Attractors.

^ massively important as architect.

NKP analysis.

N number of nodes
K number of connections
P bias (how likely the component is to communicated with another node over another.)

An attractor is a state that a system tends to move towards. E.g. for a car, an attractor is standing still, moving, crashing, etc. Some happens more often than others. Attractors are therefore a subset of states a system can be in.

How do you identify the different attractors. Random simulation. Ask business questions. What if competitor drops price, what if the eur loses value, etc. Each attractor will define a new residue. You get a bunch of them. How do you compress them into an architecture.

If a residue survives in 4 attractors, you only need to identify one of the stressors that pushes the system into one of these attractors.

Sample, Godzilla destroying Oslo is an extremely unlikely stressor. To survive this, you probably want redundancy. Redundancy is going to solve issues with your architecture that are more likely, e.g. flooding.

> Would an attractor be emergent patterns in software architecture? A pattern?

When identifying stressors, ensure that you do not fall into the pitfalls of being too technical, focusing too much on cost, thinking too small, etc.

Tricks to find stressors are using the business model canvas, using PESTLE (Political, Economic, Social, Tech, Legal and Env.), and just a pep talk (everything you're going to do is wrong and that's ok).

---

Residuality theory - "applied skepticism".

One thing that's always true about a complex system is that it'll change. However, we don't know what's going to change. The remaining system after the system has changed is the **residue**. The only thing we know about the residue is that it's going to change. And so on.

Important: It's not possible to map down the system. Cannot figure out what the change is.

The only thing you can control as an architect is what the residue is going to look like. In other words, you control how the system falls apart.

---

Can residuality theory be applies to other practices other than architecture? There _is_ evidence that this works for software architecture, but nothing conclusive.

---

# Day 2

A sample stressor for the bank exercise is Murabaha - the fact that in Islam you are not allowed to have interest.

Good architecture should not be lines and boxes (flow diagrams). It should be able to describe how information flows in the system instead. Data flow diagrams do this.

Focus on the flow of information vs the process.

---

Parnas said in 1971:

Conventional decomposition - this is bad.

If you have process a --> b --> c --> d, if you ask a CS student, they will say that the component breakdown is a --> b --> c --> d, which is bad. This means that if B changes, A and C will have to as well. This is called contagion.

Non-conventional decomposition - this is good.

Design based on what's going to change. Problem is that everything is going to change. You never know what components a stressor is going to hit. They can be decoupled and still be hit by the same stressor. 

By stressing your architecture, you find these hidden couplings!

---

Incidence matrix:

first column is trigger (stressor)
first row is function that the stressor touches
if stressor triggers function, it's a 1 in the matrix, otherwise 0.

Functions that respond the same way to stress can be put in the same component boundary.

Functions that respond to a lot of stressors might do much, or might be too important.

Stressors that touch a lot of functions need to be mitigatesd.

Functions that do not respond to any stressor are dangerous as you probably have not found the stressor that affects the function.

---

How to do the stressor analysis:

1. Identify a stressor.
2. Figure out the impact on the business. 1/2 of attractor.
3. Figure out how the business will respond. 2/2 of attractor.
4. Look at your existing architecture and figure out what it will look like after the attractor.

A common example stressor is internal server outage due to DDOS. The impact on the business will be that the service is unavailable. The business might respons with increased capacity. Based on your current architecture, the residue will be that you add a load balancer or some DDOS protection.

---

As a developer, code can be correct, as an architect you cannot be correct as you do not know what the future holds. Focus instead on criticality.

```
N
| 
|
|
|___________ K
```

Low N, K == monolith
High N, K == microservices
There's a line between N and K that's the line of criticality. This is where we want to be.
We usually start at monolith, and when we stress it, we end up closer to the line of criticality.

---

During the analysis you often encounter things you won't need or are never going to happen. This is fine, but don't let it stop your thinking just because you think it's unlikely that it's going to happen.

Argues that open conflict is bad [[dysfunction-2-fear-of-conflict]]. 

Important to distinguish between business and tech. Define where tech decisions end and business ones start. E.g. conflicting interests: money might define architecture.

ATAM. Risk management meeting to, not figure out risk, but to figure out where the line of the responsibility goes. Architect vs COO vs CFO. Some residues are going to be ignored. This is OK, but you have to make sure that the business understands the implications of the decisions. Might also change your architecture. If redundancy is ignored, you still might have changed your arch to be ready for it.

---

Failure Mode Effects Analysis: pick a component in your architecture, figure out how it can fail, figure out the impact of it failing, figure out how you detect whether it fails, figure out the higher level impact and figure out how you can mitigate it.

E.g. Queue can crash, stop, slow down. Impact is that the system stops working. We detect it by seeing that the filter component that wants to write to the queue will start complaining. The higher level impact is that the system as a whole will stop working. We can mitigate this by having a redundant queue or just have the filter component wait a little.

