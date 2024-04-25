Martin, R. C. (2021). _Clean craftsmanship: Disciplines, standards, and ethics_. Prentice Hall.

[[$Bibliography]]

A discipline will consist of an essential part and an arbitrary part, both of which are required. The essential part is the main idea behind the discipline, whereas the arbitrary part gives it some substance.

E.g. good code should consist of at least 80% unit tests. The essence is that you need to test your code to ensure that it works, the arbitrary part is 80%.

When disagreeing with a discipline, make sure that you don't just disagree with the arbitrary part.

# TDD

TDD, along with simple design, refactoring and pairing (collaborative programming) and acceptance tests form the fundamentals of software craftsmanship, however, TDD might be the most important one. 

For TDD, tests come first. Always. Not just when writing new features, but also when fixing bugs and really doing anything. Tests come first.

The essence of TDD is that you maintain a test suite that ensures that if any code passes, it will be deployable. I.e. passing tests implies deployability.

Three laws:
1. Write no production code until you write a test that fails due to the lack of the production code.
2. Only write the bare minimum of a test that is needed to make it fail. Resolve failure by writing production code.
3. Only write the bare minimum production code to make the test pass. Then write more tests. Also referred to as "don't go for the gold", implying that you should do things step by step.
4. (Refactoring). Every time you make something work, you also make it nice.

Following these laws, your workflow will now be something like 1, 2, 3, 2, 3, 2, 3... until you finish what you are working on. Initially this might seem tedious... However...

You should be bad at the tools you do not want to use often. E.e. you should be bad at using the debugger in your IDE as it's indicative of having to debug often. If you're really good at debugging, perhaps you do it too much? [[$Research]]

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

# Refactoring

Refactoring preserves behavior. This is why tests are so important. If they pass, the behavior has not changed, thus you can refactor without worrying about breaking anything.

Refactoring, cleaning up code without changing its behavior is neigh impossible without TDD. First write tests of current behavior, then write code, when tests pass again, you know you're safe. This way we know that the refactor changed nothing.

"Extract until you drop". Split methods into smaller and smaller pieces until you cannot do it anymore. This way you ensure that each function does one thing and one thing only. This makes testing easier.

Name of a function should be inversely proportional to its scope. I.e. the longer the name of a function, the more specific it is.

Thus, make sure your code reads like well written prose. This way you can _read_ your code and understand what it does, e.g. instead of

``` ts
if (a || b || c && y) {
	x.map((y) => y + z);
}
```

``` ts
if (somethingIsTrue()) {
	doSomethingSpecial();
}
```

All your functions should read like "TO paragraphs", e.g. "to do something, we need to do something else. To do something else, we need to do something entirely different. To do something entirely different, we need to ..." This is called the stepdown rule.

Extracting variables usually come before extracting methods. Sometimes also done to explain things better. E.g. instead of hardcoding a number into your method, your code is more likely to read like prose if you extract the variable. E.g. 

```ts
if (item.abv > 4.7) {
	sendToVinmonopolet();
}
```

is much easier to understand if you write:

```ts
if (alcoholLimitExceedsGroceryStoreLimit) {
	sendToVinmonopolet();
}
```

# Simple Design

