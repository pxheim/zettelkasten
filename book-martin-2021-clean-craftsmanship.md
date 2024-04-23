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
3. Only write the bare minimum production code to make the test pass. Then write more tests. Also referred to as "don't go for the gold", implying that you should do things step by step.
4. (Refactoring). Every time you make something work, you also make it nice.

Following these laws, your workflow will now be something like 1, 2, 3, 2, 3, 2, 3... until you finish what you are working on. Initially this might seem tedious... However...

> You should be bad at the tools you do not want to use often. E.e. you should be bad at using the debugger in your IDE as it's indicative of having to debug often. If you're really good at debugging, perhaps you do it too much?

When writing good tests, they will become the documentation of your code.

Writing test after the fact is pain, not just because it's boring, but also because you probably wrote the code in a way that cannot easily be tested, and thus you have to rewrite the code in order to test it. This sucks.

Boy scout rule, leave the code cleaner than what you found it, only really works if you have tests in place. Otherwise you might end up inadvertently breaking some code.

Refactoring is not something you plan for. It's not something that shows up in your sprint. It happens all the time as part of TDD. Refactoring never changes behavior, which is why it plays nicely with TDD.

Get into the habit of fail, pass, refactor, fail, pass, refactor, and so on.

3A pattern when writing tests. Arrange, Act, Assert. All tests follow this pattern, basically set up stuff, perform the action you are testing, then check if the action actually completed. This can also be converted to given when then of BDD.

Every test you write is a transition in the finite state machine that you are trying to create in your program. Your program is a finite state machine as your computer is a finite state machine processor. How do you ensure that all transition changes are tested? Well, by writing tests first!

Mezaro's formal vocabulary of test doubles:
	- Dummies: implementation of an interface that does nothing. Not terribly useful, but sometimes necessary.
	- Stubs: implementation of an interface that returns something specific in order to be used in a test.
	- Spies: same as stubs, but also remembers what was done and can be queried about it later. E.g. how many times was method x was called. Perhaps the most common test double.
	- Mocks: same as spies, but also knows what to expect, i.e. test assertions are part of the mock. Basically you can see how many times method x was called with value y, and it'll fail if value z was provided instead.
	- Fakes: Different from all the previous ones. These are fake implements some business rule that allow you to use it to test certain scenarios. E.g. for authentication it can return true for 'goodPassword' and false for 'badPassword'. Fakes are not used often. As application grows, so do fakes.

Som testing practices:
	- Do not test the database. Test the queries.
	- Do not test the UI. 


