Humble, J., & Farley, D. (2010). _Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation_. Addison-Wesley.

[[$Bibliography]]

The Deployment Pipeline is the process that takes your application from built to deploy to test to release. Will vary greatly from company to company or even app to app.

Two main components of delivering high quality software is automation and frequent releases. Automated because otherwise each release can be different and frequent in order to mitigate risk, but also get feedback often.

3 key components to good feedback from releases:
1. Every change should provide feedback.
2. Should get feedback as soon as possible.
3. Feedback must be acted upon.

Feedback most often come in the form of test results.

CI -> QA should not make their own builds, they should use production capable releases. If they build for themselves, their builds might be different from prod candidate.

Every change should lead to a potential RC. If that's not the case, why make the RC in the first place? Test & dev happen at the same time. Different from traditional dev where RC is one of the last steps in the process.

No need to automate everything at once. Incrementally is fine. Almost everything can and should be automated in the end.

