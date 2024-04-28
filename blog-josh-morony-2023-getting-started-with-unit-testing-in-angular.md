[[$Blogs]]

https://modernangular.com/articles/getting-started-with-unit-testing-in-angular

Easiest place to start is testing the inputs and outputs of your dumb components. Given some input, the component should show x. Clicking some button, should trigger y.

Do TDD! It even works in simple examples like the one given in the blog about showing a checklist or not.

Structure of most dumb component tests will be similar in the sense that we'll ARRANGE some input, and then run `detectChanges` to make sure the DOM has been updated before we ASSERT that the element we expect to be there is actually there.

```
ARRANGE
- Whatver you want the input to be.
- Add the input to the element.

ACT
- fixture.detectChanges();

ASSERT
- Check that some element of the component now exists.
```

To check that an element exists you should use a test-id or similar that is decoupled from the element. Do not use classes or other ways of finding an element as that approach is brittle. E.g. `[data-testid="some-id"]` is good.

Remember TDD principles. Write as much of a test as you can before it fails, then fix the test by writing bare minimum, then cont. writing test, and so on.

Remember to initialize your @inputs by supplying a default value to them in the beforeEach.

Observer spy: @hirez_io/observer-spy [[$Research]]

