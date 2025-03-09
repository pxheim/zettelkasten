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

[[connascence]]

[[integration-strength]]

[[module-distance]]

Distance is a measure of how close code is, both on a technical level, but also on a socio-technical level. On a technical level, code in the same statement is closer than code in two separate methods, which is again closer than code in separate classes, and so on. On a socio technical level, code made by the same team is closer than code made by two separate teams.

Components that are located close to each other area easier to change than those located far apart. This is a double edged sword, as close components also have to change when related ones change. We can say tat the distance is the inverse of lifecycle coupling.

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

There are cases where neither structured design nor connascence are able to see what should be strong coupling. E.g. a method with no dependencies that calculate whether a user should get free shipping or not.

Not possible to merge structured design & connascence. Must find a new method. Enter integration strength based on 

- Contract coupling
- Model coupling
- Functional coupling
- Intrusive coupling

Intrusive coupling is when a module communicates through, and thus depend on, the implementation details of another module, instead of going through a public interface.

Functional coupling happens if two modules are coupled by their functionality, i.e. coupled by business logic. They don't have to have a downstream / upstream relationship. Several types of functional coupling:

- Sequential functionality: things have to happen in a specific order.
- Transactional functionality: multiple operations need to all succeed for successful outcome, otherwise revert all.
- Symmetric functionality: two modules implement the same functionality. Does not mean the code needs to be the same. This is DRY, but not referring to code.

Model coupling happens when a model used by one module is also used by another. Reusing the same model across several modules can be detrimental to modular design.

Contract coupling is when two modules communicate through an integration specific model (a contract). E.g. if a model exposed also exposes multiple integration details (interfaces, enums, etc). This is bad. Can be fixed by making another model that converts all of specifics to primitives. An integration contract can be as simple as a public method that then calls private ones in a class.

Contract coupling is the "best" and where you want to end up, but not force it.

There's a chart on pg 143. that's great!

---

Be careful to consider the distance between components. Ones that are close together is easier to change together.

There's also the concept of distance, but on a socio-technical level. E.g. the distance between two components made by one team is smaller than those made by two teams.

Distance is inverse to lifecycle coupling. Components located close to one another will also affect each other's lifecycle e.g. will have to be deployed together.

---

Software changes reveal implicit coupling. E.g. a change that has a ripple effect through the system reveals implicit coupling.

Explicit coupling in components that are never expected to change is not that bad.

Conway's Law example: startups in general will make a tightly coupled system. Any change can easily be communicated. As team grows, maybe into multiple teams, their goals also change. They become more distant from each other ans will make components with greater distance. Tight coupling is now very bad.

Volatility defines how often something is expected to change. High volatility = high rate of change.

DDD's domain analysis:

- Business domain: this is the company's overall area of activity: e.g. retail, cloud computing, energy management, etc. It can be more than one.
- Subdomains: finer grained versions of business domains.

Subdomains can be further broken down into

- Core: These are the core IPs of the company. They are likely to change often. Very hard to copy. "Secret Sauce".
- Generic: Things the company needs, but that can likely be bought off the shelf.
- Supporting: Things needed that cannot be bought off the shelf. They support core or generic domains.

Consider both integration strength and volatility when designing a system. You can have a system w/ all the same integration points, but one can be much more resilient than the other if the tightly coupled integration points are between non-volatile components.

Be aware that the volatility of a supporting domain _can_ be high if it's tightly coupled to several core domains.