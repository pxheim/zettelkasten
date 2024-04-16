Branching is generally considered bad for CI as it defers integrating your changes with the rest of the application. The more branches you have the worse it is as the chance of having to deal with merge conflicts just increases.

If you have a very mature CI set up, you might be able to do without branches entirely, however, you'll most likely find that you'll need some form of branching strategy in place. It's then to still keep in mind that developers should integrate their changes as often as possible, and thus a strategy with few, short-lived branches is preferred.

[[git-branching-strategies]]
