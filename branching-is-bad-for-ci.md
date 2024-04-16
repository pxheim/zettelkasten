Branching is generally considered bad for CI and, if you have a very mature CI set up, you might be able to do without them. However, you'll most likely find that you'll need some form of branching strategy in place. It's important to still keep in mind that you

Branching is bad because
- Breaks with the principles of CI, e.g. it defers merging -- integrating your changes.
- Many branches == more bad.
- Merge conflicts.
- Hard to refactor codebase when it touches a lot of code.