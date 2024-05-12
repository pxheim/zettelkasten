Branching is generally considered bad for CI as it defers integrating your changes with the rest of the application. The more branches you have the worse it is as the chance of having to deal with merge conflicts just increases.

The only real exception to this should be release branches, which can be long lived to keep track of specific versions. Note that these are never integrated. It's common to tag a release branch when a release is actually made.

If you have a very mature CI set up, you might be able to do without branches entirely, however, you'll most likely find that you'll need some form of branching strategy in place. It's then to still keep in mind that developers should integrate their changes as often as possible, and thus a strategy with few, short-lived branches is preferred.

Two other common branching strategies are branching by feature and branching by team. Very short lived feature branches, and team branches if each team are working on distinct stories can work, however they should ideally be avoided if possible

It's always better to start off by not branching, and then introducing branching if you really truly have to in the future.

[[git-branching-strategies]]
