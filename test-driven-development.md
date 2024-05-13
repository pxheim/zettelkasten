Test driven development means that you write tests first, which fails, then the code to make it pass. You'll do this for everything; bugs, features, anything. Writing test after the fact is pain, not just because it's boring, but also because you probably wrote the code in a way that cannot easily be tested, and thus you have to rewrite the code in order to test it.

The three laws of TDD is:

1. Write no production code until you write a test that fails due to the lack of the production code.
2. Only write the bare minimum of a test that is needed to make it fail. Resolve failure by writing production code.
3. Only write the bare minimum production code to make the test pass. Then write more tests. Also referred to as "don't go for the gold", implying that you should do things step by step.
4. (Refactoring). Every time you make something work, you also make it nice.

Following these laws, your workflow will now be something like 1, 2, 3, 2, 3, 2, 3... until you finish what you are working on. The essence of this is that you maintain a test suite that ensures that if any code passes, it will be deployable. I.e. passing tests implies deployability.

Test driven development is arguably the most important of the [[software-craftsmanship]] pillars. When writing good tests, they will become the documentation of your code. Designing tests is just as important as designing production code. If care is not taken, you'll end up with fragile tests (tests that are too coupled to code) that will break often.
