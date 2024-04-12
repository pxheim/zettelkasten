Binaries should only be created once in the deployment pipeline, then use the same binary throughout the deployment pipeline. If you build multiple times, it's hard to guarantee that t


Never recreate binaries within the deployment pipeline. Build once and use the same binary throughout. Do not store these in VCS.

CI -> QA should not make their own builds, they should use production capable releases. If they build for themselves, their builds might be different from prod candidate.