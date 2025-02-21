Dalmijn, M. (2023). _Driving Value with Sprint Goals: Humble Plans: Exceptional Results_. Addison-Wesley.

[[$Bibliography]]

# Overview Notes

[[agile-planning-friction]]

[[$Overview]]

Understanding the fundamental gaps and friction in agile planning, and how traditional responses often worsen these issues rather than resolve them.

Links:
- [[friction-knowledge-gap]]
- [[friction-alignment-gap]]
- [[friction-effects-gap]]
- [[complex-domain-planning]]

# Atomic Notes

---

[[friction-knowledge-gap]]

The knowledge gap represents the difference between what we know and what we'd like to know. The common response of increasing planning when lacking information is counterproductive, as effective planning requires knowledge. Instead, act on current knowledge while explicitly working to discover unknowns.

Links:
- [[complex-domain-planning]]
- [[humble-planning-principle]]

---

[[friction-alignment-gap]]

The alignment gap occurs between desired and actual behaviors. Responding with more detailed instructions often increases misalignment rather than reducing it. This connects to the principle of leading with intent rather than specific directives.

Links:
- [[intent-based-leadership]]
- [[friction-effects-gap]]

---

[[friction-effects-gap]]

The difference between expected and actual outcomes of our actions. Tightening control and reducing autonomy typically widens this gap rather than closing it, especially when working with experts.

Links:
- [[intent-based-leadership]]
- [[humble-planning-principle]]

---

[[complex-domain-planning]]

In the Cynefin framework context, mistaking complex domains for merely complicated ones leads to overconfident planning based on assumed knowledge. The solution is to make humble, small plans that help discover the true nature of the complex domain.

Links:
- [[humble-planning-principle]]
- [[friction-knowledge-gap]]

---

[[intent-based-leadership]]

Leading with intent involves communicating desired outcomes rather than prescribing specific actions. This approach leverages expert knowledge and allows teams to determine the best path to achieve goals.

Links:
- [[sprint-goal-principles]]
- [[friction-alignment-gap]]

---

[[goal-hierarchy]]

A clear hierarchy of goals drives agile planning: Product goals guide the creation of sprint goals, which in turn guide daily work. This separation of intent from specific plans allows for adaptation while maintaining focus on desired outcomes.

Links:
- [[sprint-goal-principles]]
- [[agile-goal-importance]]

---

[[agile-goal-importance]]

Without clear goals, teams default to output-focus rather than outcome-focus. This leads to treating all work as equally important (effectively making nothing important) and often results in accumulated technical debt.

Links:
- [[sprint-goal-principles]]
- [[value-over-features]]

---

[[sprint-goal-principles]]

Effective sprint goals follow the FOCUS framework:
- Fun (memorable)
- Outcome-oriented
- Collaborative
- Ultimate (includes why)
- Singular (avoid competing priorities)

Links:
- [[agile-goal-importance]]
- [[agile-planning-approaches]]

---

[[agile-planning-approaches]]

Two contrasting approaches to sprint planning:
- Anaconda-scrum: Comprehensive upfront planning, rigid sprint scope
- Hummingbird-scrum: Flexible planning focused on sprint goal, adaptable scope

Links:
- [[sprint-goal-principles]]
- [[capacity-planning-flexibility]]

---

[[capacity-planning-flexibility]]

Avoid planning for 100% capacity, as this eliminates flexibility. Focus on meeting the sprint goal first, then take on additional work if possible. Task carryover is acceptable if the goal is met.

Links:
- [[agile-planning-approaches]]
- [[value-over-features]]

---

[[value-over-features]]

Value cannot be reliably predicted before feature implementation. Feature factories risk producing output without value. Focus on measuring and validating actual customer value rather than feature quantity.

Links:
- [[north-star-metrics]]
- [[product-vision-guidance]]

---

[[north-star-metrics]]

A framework for measuring customer value through:
1. Identifying a primary metric driving customer and business value
2. Determining input metrics that influence the north star
3. Focusing on features that positively impact input metrics
4. Regular validation of the entire metric chain

Links:
- [[value-over-features]]
- [[product-vision-guidance]]

---

[[product-vision-guidance]]

A clear product vision provides direction and enables confident decision-making about feature requests. It serves as a filter for maintaining focus on valuable work.

Links:
- [[value-over-features]]
- [[north-star-metrics]]

---

[[agile-pragmatism]]

Practical guidelines for maintaining agility:
- Avoid spikes when unknowns can be discovered during feature development
- Treat the backlog like fresh milk, not a wish list
- Don't over-formalize interruption handling
- Balance Definition of Ready and burndown precision with flexibility
- Embrace uncertainty as natural

Links:
- [[complex-domain-planning]]
- [[humble-planning-principle]]

# Literature Notes

Friction is what's preventing you from achieving your plan. There are three gaps that are amplified by friction:

- Knowledge gap: difference between what we know and what we'd like to know.
- Alignment gap: difference between what we'd like people to do and what they actually do.
- Effects gap: difference between what we expect our actions to achieve vs. what they actually achieve.

To resolve the gaps, we often do the opposite of what would solve it:

- Knowledge gap: we don't have enough info so we plan more. Cannot plan w/o knowledge, so we act on what we believe we know.
- Alignment gap: we issue more instructions.
- Effects gap: we tighten control of people's autonomy. E.g. CS person that must go through step-by-step troubleshooting.
Start with what you do know and figure out what you don't know.

---

Considering the cynefin framework, it is dangerous to think you are in the complicated domain when you are actually working with the complex domain. When you make plans here, you plan based on things you think you know, but in fact you do not. Make humble (small) plans to discover more and more about the complex domain you are in so that you eventually find yourself in the complicated domain.

---

When you lead with intent, you tell people what you intent to do, i.e. the outcome you would like to achieve. The people will then figure out what the best course of action is to get to this goal. When working with experts, you're likely to get a better result if you do this vs. if you tell them what to do, as they most likely know better than you.

---

The product backlog should have a product goal, similar to how the sprint backlog has a sprint goal. The product goal drives the creation of the sprint goal.

Setting a goal separates intent from the plan. When we learn more after starting the sprint, we can adjust the plan to still meet the intent.

---

If you don't set a sprint goal, there's no outcome to focus on, and instead, the only possible focus is the output.

W/o a goal, everything becomes equally important, but then, as they saying goes, nothing is important.

No goal ==> tech debt. If time, cost and scope are fixed and the team has to cut something, quality will suffer. If we can reduce the scope and still meet the goa, we're good.

---

Anaconda-scrum: plan as much as possible before starting a spring. The sprint is not flexible. Cannot add / remove work.

Hummingbird scrum: plan only tasks rel. to sprint goal, everything else is added later. Sprint is just a checkpoint where we see how we are doing.

---

A sprint goal should follow the FOCUS mnemonic:

- Fun (or memorable): give it a title that people can remember. This is optional.
- Outcome-oriented: focus on what you are trying to accomplish, not how, as this can change.
- Collaborative: to ensure buy-in, the goal should be made together w/ the team.
- Ultimate: must include a "why".
- Singular: have only one. Competing goals are like saying multiple things are most important, which cannot be true.

---

Don't plan for 100% capacity. Leaves no room for flexibility. Focus on meeting the goal, grab some new tasks, and if they carry over, that's OK.

Sprint review is not about demoing what has been done. Those things are already live and we're gathering feedback on them, so why show them again? Instead talk about:

- Do we believe we made value?
- Inspect product increment.
- What to do next.

Retrospectives facilitate double-loop learning, we get feedback on features, to provide feedback on how we work.

---

It's almost impossible to tell what'll become valuable before you have made it. It's not about the features you build, but how they are received.

Feature factories produce many features w/o considering the value of these features. In scrum, it's easy to assume that all proposed features will give value.

Don't focus on output, instead focus on how you're producing value for the customer. Measure this value! How? NPS?

---

**North start metric, a way to measure that your features actually produce value to your customers. First, identify a north start metric, this is something that you know drives customer and business value. Then identify the input metrics that positively influence your north star. The features you want to work on are the ones that influence the input metrics, that in turn influence the north start metric.**

While you should frequently monitor whether features influence inputs and whether inputs push the north star in a positive direction, you should also evaluate whether the north star _actually_ drive customer and business value.

---

Create a product vision. This is the direction you wish to tak your product. It therefore enables you to say no to feature requests if they don't align with your vision.

---

If you can figure out the unknowns while building a feature, you don't need a spike for it.

Treaty your backlog like fresh milk. Do not add everything to it. No point in making it a Christmas wish list.

Don't make plans for things that don't deliver value. E.g. don't add activities that fall outside the work you're doing in the sprint. Typically things like interruptions.

DoR is good, but don't be too fixated on it.

Burndown charts are good, but don't be too fixated on them being perfect.

Learn to live with uncertainty.

---

Working on three things at once and finishing them late vs working on one , finishing one, etc. Stakeholders don't like this. Tell them about compounding interest. Another example is focusing on flow vs focusing on resource utilization.

PO should _not_ decide on the sprint goal. The team should decide, ofc. w/ PO input.
