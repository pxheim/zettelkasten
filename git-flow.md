A git branching strategy that is based on having a *master* branch with production code, a *develop* branch with code that's in development, *feature* branches for features that are in progress, *release* branches to track releases, and *hotfix* branches to track hotfixes.

Normal workflow is to start a feature branch based off the develop branch and use the `feature/` prefix. When the feature is complete, a PR is created and the feature is eventually merged into develop.

Release branches are created from the develop branch and use the `release/` prefix. Commits to the release branch should only be fixes for the release, and each commit is merged back into the develop branch.

When releases go to production they will be merged into the master branch, but also the develop branch.

If an issue arises on the master branch, a hotfix branch is created from the master branch using the `hotfix/` prefix. After the fix, this branch is merged into both master and develop.

[[git-branching-strategies]]