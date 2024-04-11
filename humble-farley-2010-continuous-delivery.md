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

If there's some process in dev that "hurts", it's often tempting to stop doing it, or do it less. Releasing is typically one of these things. Wrong approach, the things that "hurt", do them more. That's the only way they will hurt less.

"Done" means released to production. If it's not, then it's not done. This means that a developer alone cannot make something some. The whole team w/ QA has to. Everybody is responsible for the delivery process.

A good configuration management must
- Exactly reproduce any environment you have for your application.
- Allow incremental changes to any of your environments.
- See and track all changes done to any environment.
- Satisfy all compliance regulations.
- Make it easy for all team members to get all the information they need and make the changes they need to make.

Branching is bad because
- Breaks with the principles of CI, e.g. it defers merging -- integrating your changes.
- Many branches == more bad.
- Merge conflicts.
- Hard to refactor codebase when it touches a lot of code.

CI only works w/ long commit messages describing what you did in detail. ALSO link to JIRA task or similar. This applies to our PRs more than commits in "our flow".

Checking in all your ext. libraries to VCS is prob not going to work, but good idea to keep a separate repo w/ the dependencies. App can then get the dependencies from there.

Configuration management is all about keeping your config files, e.g. package.json, env. pubspec, or similar in VCS so that they can be used to set up same env. when new person starts or you wish to check out an older version.

CI requires a shift in thinking. Traditionally your application is broken until you prove that it's not (through tests, etc.). With CI, your application is always assumed to be working until it's not.

CI requires at minimum three things:
1. Everything must be in VSC.
2. One click build & test from CLI.
3. Team must agree on doing it.

Simplified 7 step workflow for CI:
1. Wait for current build to succeed.
2. Update your code /w origin.
3. Ensure local code runs w/ changes.
4. Commit your changes.
5. Wait for CI to check your changes.
	1. Fail: Fix and go to step 3
	2. Pass: Rejoice!









The 5 step process for improving cycle time is:

1. Identify the constraint.
2. Exploit the constraint, i.e. set them up for success.
3. Subordinate others, i.e. force others to help out wherever possible.
4. Elevate the constraint, i.e. hire more people, add more compute power, etc.
5. Start from 1 again.
