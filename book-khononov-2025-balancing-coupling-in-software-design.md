Khononov, V. (2025). _Balancing Coupling in Software Design: Universal Design Principles for Architecting Modular Software Systems_. Pearson Education.

[[$Bibliography]]

# Overview Notes

# Atomic Notes

[[accidental-and-deliberate-coupling]]

There are two ways coupling can manifest itself in software, deliberate and accidental. The first is coupling you need. Just like a watch will not be able to function without the components interacting with one another, software will not either. Accidental coupling, however, is coupling that you wish to avoid. This leads to complex systems. 

[[global-complexity]]

The complexity of a system as a whole is it's global complexity. A system comprised of only interconnected microservices is likely to have high complexity.

Links:

[[local-complexity]]

[[local-complexity]]

Local complexity can be defined as the complexity within a module. The extreme example of this would be viewing a monolith as a single module, in which case the local complexity would be extreme.

Links:

- [[definition-of-module]]

[[definition-of-module]]

The words "module" and "component" are often used interchangeable to mean the same thing. To avoid confusion, we define module as "a boundary encompassing a well defined functionality exposed to the system". A module can be a class, a service, a method, or whatever, as long as it meets this definition.

A module can be broken down into:

- Function: it's public API that is exposed to the rest of the system.
- Logic: it's internal implementation.
- Context: it's dependency on execution environment.

A module should have high cohesion, which means that the content inside the module should be tightly coupled. If not, it's likely a sign that the module should be split.

Links:

- [[modular-design]]

[[modular-design]]

Based on the [[definition-of-module]], it should follow that "modular design" is a system comprised of well defined modules, but it's not that simple. Breaking a monolith down into multiple well defined modules might not make for a better system. It might in fact make things worse.

**A modular system is defined by "the arrows between the boxes", i.e. how the different modules interact with one another.**

Links:

- [[definition-of-module]]

# Literature Notes

Coupling is unavoidable if you want your system to have a purpose. It's the interplay between components that create purpose, e.g. a clock, the components need to interact for it to work. Coupling is not synonymous w/ bad design. Sometimes you need it, but it should be deliberate.

Accidental and deliberate (essential) coupling, we want to avoid the first, and we need the latter for the system to work.

---

Good examples on the Cynefin framework

**In the complex domain, you need to perform experiments to uncover the unknowns until you eventually find yourself in the complicated domain.**

---

Local complexity is complexity within a module. Global complexity is the complexity between a system's modules.

Constraining degrees of freedom reduces coupling at the expense of flexibility. Always evaluate which one you value the most for the given design.

Take care not to only evaluate local or global complexity. Always look at both.

---

"Module" and "Component" will be used interchangeably. Define module as "a boundary encompassing a well defined functionality, exposed to the system". Can be class, service, function, whatever. It then follows that modular system is a system comprised of well defined modules.

However, not always the case. Breaking down a monolith into small microservices does not necessarily make for a module system, it might in fact make it worse.

A module can be broken down into

- Function: it's public API, it's reason for existing, it's purpose.
- Logic: it's internal implementation.
- Context: it's dependency on execution environment.

Good modules are good abstractions. Ostenhout refers to this as deep modules. The more implementation detail is hidden, the deeper the module.

A bad abstraction exposes too much information or fails to expose critical information.

A modular system is defined  by the arrows between the boxes, not what's inside the boxes.

A module should have high cohesion, i.e. the content inside a module should be tightly coupled. If not, might be a sign that the module should be split into multiple modules.

---

Structured design methodoloty, old method of identifying coupling. Outdated, but parts are relevant today. It defines 6 main types of coupling:

- Content coupling: one class uses the data directly from another class.
- Common coupling: classes are coupled through the use of a global state, i.e. all of their internal state is global.
- External coupling: same as common, but no the whole state is shared.
- Control coupling: how the implem