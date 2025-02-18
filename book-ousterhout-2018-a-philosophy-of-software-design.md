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

Different layer, different abstraction. Each layer must provide a useful new level of abstraction. Pass through methods are a sign og this _not_ being the case (OK for decorators, but barely). Also adjacent layers w/ similar abstractions = bad.

Interface should always be different from implementation. Otherwise there's no abstraction provided by the module.

Eliminating pass-through variables can be hard. Possible to use context (global state), or try to design away from it. Not always possible / feasible.

---

Pull complexity down (into the implementation, away from interface). It's better for one dev to deal w/ complexity vs. many using the interface.

---

Bringing together & splitting code, always consider the complexity.

Bring together if:

- Reduces code duplication
- Makes interface simpler
- Information is shared between modules

Separate if

- Contains general and special purpose code.

Splitting methods, someone states max 20 lines, or as short as possible. However, not always correct, increases complexity.

A method should do one thing and one thing completely.

Split methods into atomic subtasks, meaning the subtask is a (relatively) general purpose method.

If you cannot understand the implementation of a method w/o looking at another one, it's a red flag --> conjoined methods.

---

Design your interfaces so that errors are defined away.

Mask errors by handling them at a lower level.

Aggregate errors if there are many errors all over the palce.

Sometimes just crashing is the best option.

---

Your first design is rarely the best. Design two or more variations of the interface you are making, pick the best one.

---

Fallacy: good code does not need comments. A method's abstraction w/o comments is its declaration only. You should not have to read the code of a method to understand what it does.

Invest time in keeping comments up to date. It pays off in the long run.

Comments capture what was in the mind of the developer that cannot be represented in code. Helps w/ cognitive load & unknown unknowns.

Comments are not always a place to extract other methods. Only if it makes sense (Uncle Bob).

---

Comments should describe things that aren't obvious from code. Good ex. is whether start or end are inclusive indexes.

4 main types of comments

- Interface: before a class, method, etc.
- Data structure member (before a variable).
- Implementation comment (often unnecessary)
- Cross module.

Interface and data structure member comments are the most important. All interfaces and all variables should be commented. Almost w/o exception.

Implementation comments often just repeat the code. Avoid.

Good comments use different words in the comment than those used in the variable / method names.

Documenting variables (not local ones. They are most often self-explanatory) should focus on what the variable represents, not how it's manipulated. 

Since abstractions cannot be explained by code, you must comment on them!

Interface comments should never have to explain implementation. Makes it shallow.

Implementation comments should only explain what (or why) the code is doing, not how.

Implementation comments can help split code into blocks / phases to assist navigating. Comments before loops are also helpful.

---

Names should be as specific as possible w/o becoming unwieldy and long. 2-3 words are optimal, but not a restriction.

If it's hard to come up with a name, it could be a sign of complex code.

---

Write comments before code (CDD?). Improves design, prevents comment backlog.

Use comments as a design tool. If something requires a long comment or is hard to describe, it most likely indicates complexity or incorrect abstraction.

---

Resist making quick fixes to your code. Always stay strategic, not tactile. If you're not making the design better, you're probably making it worse.

---

Ensure consistency by establishing a style-guide. Write scripts to follow it if necessary. Consistency also means doing dissimilar things differently. Do not enforce consistency when it does not work.

---

Code should be obvious. The reader of the code decides whether it's obvious or not, not you.

Avoid generic contains for passing data around. Take the time to make a specialized structure, class, interface, etc.

---

OOP is good, but be wary of the coupling generated by inheritance. Use composition instead where possible.

Agile, be wary of tactical programming becoming the norm. The increments of development should be abstractions, not features [[$Research]]

TDD is bad all the way. Encourages tactical programming vs structural. Unit tests are immensely important still.

---

Developers are terrible at knowing what is performant or not, so always measure.

If you need to refactor a large piece, first design around the ideal path, then add the exceptions later. Ideally you have one `if` at start that catches all special cases before executing the general case.
