Test driven development means that you write tests first, which fails, then the code to make it pass. You'll do this for everything; bugs, features, anything. The three laws of TDD is:

1. Write no production code until you write a test that fails due to the lack of the production code.
2. Only write the bare minimum of a test that is needed to make it fail. Resolve failure by writing production code.
3. Only write the bare minimum production code to make the test pass. Then write more tests. Also referred to as "don't go for the gold", implying that you should do things step by step.
4. (Refactoring). Every time you make something work, you also make it nice.

Following these laws, your workflow will now be something like 1, 2, 3, 2, 3, 2, 3... until you finish what you are working on. The essence of this is that you maintain a test suite that ensures that if any code passes, it will be deployable. I.e. passing tests implies deployability.

Test driven development is arguably the most important of the [[software-craftsmanship]] pillars.









When writing good tests, they will become the documentation of your code.

Writing test after the fact is pain, not just because it's boring, but also because you probably wrote the code in a way that cannot easily be tested, and thus you have to rewrite the code in order to test it. This sucks.

Boy scout rule, leave the code cleaner than what you found it, only really works if you have tests in place. Otherwise you might end up inadvertently breaking some code.

Refactoring is not something you plan for. It's not something that shows up in your sprint. It happens all the time as part of TDD. Refactoring never changes behavior, which is why it plays nicely with TDD.



Every test you write is a transition in the finite state machine that you are trying to create in your program. Your program is a finite state machine as your computer is a finite state machine processor. How do you ensure that all transition changes are tested? Well, by writing tests first!

Mezaro's formal vocabulary of test doubles:
	- Dummies: implementation of an interface that does nothing. Not terribly useful, but sometimes necessary.
	- Stubs: implementation of an interface that returns something specific in order to be used in a test.
	- Spies: same as stubs, but also remembers what was done and can be queried about it later. E.g. how many times was method x was called. Perhaps the most common test double.
	- Mocks: same as spies, but also knows what to expect, i.e. test assertions are part of the mock. Basically you can see how many times method x was called with value y, and it'll fail if value z was provided instead.
	- Fakes: Different from all the previous ones. These are fake implements some business rule that allow you to use it to test certain scenarios. E.g. for authentication it can return true for 'goodPassword' and false for 'badPassword'. Fakes are not used often. As application grows, so do fakes.

Some testing practices:
	- Do not test the database. Test the queries.
	- Do not test the UI. Split into smart / dumb components and test the smart ones, or alternatively wherever the business logic is kept (view model, cubit, etc.)

Designing tests is just as important as designing production code. If care is not taken, you'll end up with fragile tests (tests that are too coupled to code) that will break often.

It's a bad idea to have any module or class x have a corresponding test class x.test. This couples the test file with the module whereas in reality the testing of x might depend on y and z. Thus, decouple the structure of your tests with the structure of your production code. [[$Research]]

When testing a class, try as much as possible to make your test not depend on the other classes that the class you want to test depend on. E.g. if you have a class x that depends on a class y, save from instantiating the class y, your tests for class x should not know about the details of class y. The same applies to private methods that are part of class x. By testing the public ones, you should be able to assert that the private ones also do what they are supposed to.

The more tests you add, the more specific they get. While doing this the production code should become more and more generic. This process of making it more generic often happens in the refactoring step.

The act of making your code more generic can be summarized in several specific steps.
- {} --> Null: Given that you start with a method that does nothing, you can make it more general by actually returning something, in this case null.
- null --> constant: returning a constant from null is usually the nest step that makes a test pass.
- constant --> variable: to make the test more generic, we can convert constants into variables in the code.
- unconditional --> selection: instead of making all your code run for all inputs, you can add an if statement to narrow the scope. Take care not to make it too narrow.
- value --> list: a list is a more complex container that can hold more information vs. a single variable, thus making it more generic.
- selection --> iteration: converting if statements to while / for loops.
- statement --> recursion: 
- value --> mutated value:

If one of these transformation leads you down a path that is suboptimal, backtrack and try another one. The order presented above is usually the preferred order in which you should perform the transformations. Always try to do the simples transformation before moving the the more complex ones. Do not skip steps as it can lead you to missing tests.