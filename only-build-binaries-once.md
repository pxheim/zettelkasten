Binaries should only be created once in the deployment pipeline, then use the same binary throughout the deployment pipeline. If you build multiple times, it's hard to guarantee that the builds are identical, thus you might introduce sources of error.

Following this logic, QA should never make their own builds. They should always use the builds that are flowing through the deployment pipeline.

Do not store the builds in VCS.
