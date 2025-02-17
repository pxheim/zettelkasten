[[$Bibliography]]

Premise: software has almost no limitation outside of complexity growing. Developers should always aim to reduce complexity. Two types: code and architecture.

---

Complexity is defined as anything rel. to the structure of code that makes it hard to understand _and_ modify.

Complexity is easier to see in other people's code vs. your own. If another dev. finds your code complex, then it is.

3 symptoms of complexity:

- Change amplification: a simple change requires modifying a lot of code.
- Cognitive load: in order to make a change, you need to know a lot about the system / know it intimately.
- Unknown unknowns: it's unknown what the code needs to be modified to make a change. This is the worst.

Opposide of ^ 2 and 3 is to be obvious.

Complexity is caused by dependencies & obscurity. The first leads to change amplification and cognitive load, the second to cognitive load & unknown unknowns... The worst...

Complexity is incremental. Stop it before it spreads.

A tactical programmer gets things done fast, but does not consider design. Tactical tornado is a dev that's excellent at this.

Strategic programmer keeps great design in mind and does invest in finding the best solution, not just one that works.

Be a strategic programmer. Invest abt. 20% of your time on making good designs (reducing complexity).

---

An interface should include all information needed for a dev to use a module.

A dev working on a module needs to know its interface & implementation, but also the interface of all modules it depends on.

Prefer deep modules; modules w/ small interfaces that hide complex implementations.

Shall modules have large interfaces and often equally (small) implementations. Avoid. E.g. a method might actually create complexity if it's sufficiently shallow.

Focusing on small modules often leads to classitis. Small < deep is often better. Often represented by methods being as small as possible, often less than x lines.

Interfaces should be designed to make the common case as simple as possible.

---

Shallow modules hide as much information as possible, while leak as little as possible.

Marking something as private while making it accessible through a getter / setter does not hide it.

Back-door leakage is dangerous: leakage that's not exposed through the interface. Example used: depending on file format.

Temporal decomposition (first we do x, then we do y...) is a common place to see information leakage / shallow modules. E.g. first we get data, then we parse it, then... etc. Focus on a module's capabilities vs. order of operation.

Making classes larger can improve information hiding.

Take care not to expose internal data structures through methods. E.g. a method returning params as a Map exposes that params are stored as a Map. Return primitives instead.

---

Design modules to be mostly general purpose, it's almost always better.

Questions to ask yourself when making modules

- Can I simplify the interface and still have it do everything I want? Reduce the API where possible.
- Will this method be used only in one place? Might be too specific if yes.
- Is the API easy for my current needs? It may be simple and used multiple places, but if its hard to use, maybe warrants redesign.

Push specification upwards or downwards, do not just mix it everywhere. E.g. specific UI things can go in a component, vs. driver related things should go in a layer below your service.

Design away special cases & checks. If you find yourself checking if x exists all over the place, redesign so that it always exists.

---

