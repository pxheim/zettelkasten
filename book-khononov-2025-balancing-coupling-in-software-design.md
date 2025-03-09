Khononov, V. (2025). _Balancing Coupling in Software Design: Universal Design Principles for Architecting Modular Software Systems_. Pearson Education.

[[$Bibliography]]

# Overview Notes

# Atomic Notes

[[accidental-and-deliberate-coupling]]

[[global-complexity]]

[[local-complexity]]

[[definition-of-module]]

[[modular-design]]

[[structured-design]]

Structured Design is a methodology used to identify coupling between modules. It's largely outdated, but it has served as a building block for better methodologies.

It defines 6 different types of coupling, ranging from high(bad) to low(good):

1. Content coupling: when one class uses the data directly from another class. The are coupled through their content.
2. Common coupling: classes are coupled through the use of a global (common) state.
3. External coupling: classes are coupled through the use of an external state. Basically the same as #2, just that the state is not global.
4. Control coupling: classes are coupled by their implementation details. E.g. a method exposes how another method is to be executed.
5. Stamp coupling: classes are coupled by shared data structure. E.g. a method exposing the Customer data structure through getCustomer instead of a primitive through getStatus.
6. Data coupling: classes are barely coupled and integrate only by sharing as little information as possible, and only through explicitly defined interfaces (contracts).

Links:

- [[connascence]]
- [[integration-strength]]

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

Structured design methodoloty, old method of identifying coupling. Outdated, but parts are relevant today. It defines 6 main types of coupling, from high (bad) to low (good):

- Content coupling: one class uses the data directly from another class.
- Common coupling: classes are coupled through the use of a global state, i.e. all of their internal state is global.
- External coupling: same as common, but no the whole state is shared.
- Control coupling: how the implementation details of one component works is determined by another. E.g. method exposes how the method is to be executed.
- Stamp coupling: when data structures are exposed that are not needed. E.g. exposing getCustomer vs getStatus.
- Data coupling: modules integrate by sharing as little information as possible and only through explicitly defined interfaces.

---

Connascence is a way to describe how something is connected. E.g. connascence by name means that something is connected by name. This can be used to explain how software modules are connected. 

We can split connascence into static and dynamic. The highest level of static connascence is lower than the lowest level of dynamic connascence. From low to high, static connascence:

- by name: a naming change somewhere results in a naming change being required somewhere else.
- by type: when two modules have to agree on using the same type.
- of meaning: when two modules attribute meaning to some arbitrary value. E.g. the same magic number being used in two modules.
- of algorithm: when two modules have to agree on using the same algorithm or protocol to understand the values transmitted between them. E.g. two modules that have to agree on which type of encryption to use.
- by position: when the order of something matters, e.g. the order of input parameters.

and dynamic:

- of execution: when the execution of something needs to follow a specific order. E.g. first A, then B, then C.
- of timing: when execution needs  to have a specific interval between them.
- of value: when a change in a value requires a change in another.
- of identity: when two objects are dependent on the exact instance of a third object.





Connascence is a way to describe how something is connected. E.g. connascence by name = modules are connected by some name. Connascence is split into static and dynamic.

Static, ranging from low (good) to high (bad):

- by name: a naming change somewhere must result in a naming change elsewhere.
- by type: when two components have to agree on using the same type
- of meaning: when two components attribute meaning to a value, e.g. magic numbers.
- of algorithm: agree on using the same algorithm or protocol
- by position: when the order of something matters, e.g. input order of fields.

Dynamic, ranging from low (good) to high(bad)

- of execution: when execution of something needs to follow a specific order.
- of timing: when execution is needed to have a specific interval between them.
- of value: when a change in a value requires a change in another.
- of identity: when two objects are dependent on an exact instance of a third one.

When evaluating connascence, a module is said to have a connascence of the highest type present.

Connascence cannot (and should not) always be reduced. Do not treat it as a design tool.

Connascence and structured design coupling explain different types of coupling in modules. Whereas content coupling is the strongest form of coupling, from connascence perspective it's the weakest.

---
