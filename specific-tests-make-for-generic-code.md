While doing [[test-driven-development]], the more tests you add, the more specific they get. While doing this, the code should become more and more generic. This process of making it more generic often happens in the refactoring step.

The act of making your code more generic can be summarized in several specific steps:

- **{} --> null**: Given that you start with a method that does nothing, you can make it more generic by actually returning something, in this case null.
- **null --> constant**: returning a constant from null is usually the nest step that makes a test pass.
- **constant --> variable**: to make the test more generic, we can convert constants into variables in the code.
- **unconditional --> selection**: instead of making all your code run for all inputs, you can add an if statement to narrow the scope. Take care not to make it too narrow.
- **value --> list**: a list is a more complex container that can hold more information vs. a single variable, thus making it more generic.
- **selection --> iteration**: converting if statements to while / for loops.
- **statement --> recursion**: 
- **value --> mutated value**:

If one of these transformation leads you down a path that is suboptimal, backtrack and try another one. The order presented above is usually the preferred order in which you should perform the transformations. Always try to do the simplest transformation before moving to the more complex ones.

Do not skip steps as it can lead you to missing tests.
