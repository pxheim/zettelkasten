Martin, R. C. (2021). _Clean craftsmanship: Disciplines, standards, and ethics_. Prentice Hall.

[[$Bibliography]]

A discipline will consist of an essential part and an arbitrary part, both of which are required. The essential part is the main idea behind the discipline, whereas the arbitrary part gives it some substance.

E.g. good code should consist of at least 80% unit tests. The essence is that you need to test your code to ensure that it works, the arbitrary part is 80%.

When disagreeing with a discipline, make sure that you don't just disagree with the arbitrary part.

TDD, along with simple design, refactoring and pairing (collaborative programming) and acceptance tests form the fundamentals of software craftsmanship, however, TDD might be the most important one. 

For TDD, tests come first. Always. Not just when writing new features, but also when fixing bugs and really doing anything. Tests come first.

Refactoring, cleaning up code without changing its behavior is neigh impossible without TDD. First write tests of current behavior, then write code, when tests pass again, you know you're safe. This way we know that the refactor changed nothing.

The essence of TDD is that you maintain a test suite that ensures that if any code passes, it will be deployable. I.e. passing tests implies deployability.

Three laws:
1. Write no production code until you write a test that fails due to the lack of the production code.
2. Only write the bare minimum of a test that is needed to make it fail. Resolve failure by writing production code.
3. Only write the bare minimum production code to make the test pass. Then write more tests.

Following these laws, your workflow will now be something like 1, 2, 3, 2, 3, 2, 3... until you finish what you are working on.



