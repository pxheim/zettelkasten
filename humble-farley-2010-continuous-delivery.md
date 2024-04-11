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

Unit tests small pieces of your application in isolation, i.e. a method. These are the fastes and cheapest tests to run.

Component tests test the behavior of several components in your application.

Acceptance tests test against business criteria. Test against the whole app.

Tests must be kept short. If they are not, consider splitting your test process, e.g. one for building & unit tests and another for integration / acceptance.

Lock down versions, even minor ones, to ensure we always have the same dev. environment.

Reporting from CI must be very visible, especially when working as a distributed team. Also make it fun!

Humble and Farley mention that discipline is extremely important for efficient CI. This contradicts setting up env. where you have to use little willpower.

Always run at least some tests locally before committing. Ensures you don't break the build unnecessarily or waste CI resources.

Never go home on a broken build. Fit it or revert it.

Set a time limit for how long someone is allowed to try to fix their build before reverting.

Good test coverage is a requirement for CI, thus TDD is almost a must.

Consider failing builds on things like styleguide issues, warnings, builds taking too long, tests taking too long, etc.

Self thought: PRs are generally anti-CI, but are a necessity. They MUST be kept small. Break down tasks & split PRs by using feature flags, abstractions, etc. Reserve time for deep focus on reviewing PRs.

For CI to work efficiently, QA needs to work alongside developers. Define a testing strategy.

The testing quadrant
- [ ] Add this.

Happy path is when user does exactly what is intended and no errors occur. Also know as "given", "when", "then". Opposite of sad path.

Automated acceptance tests can be costly to maintain, and can create quite the overhead. A good middle ground is to make automated acceptance tests for all happy paths mixed with 80% unit test coverage and some acceptance tests for the most important flows. This is the best starting point.

Dialog w/ QA is important to automate all the most common acceptance tests.

Three main types of tests that are made by and for developers, unit, component and deployment tests.

Business facing critique tests often involve testing or showcasing completed features to get feedback for changes.

Nonfunctional acceptance tests test things that are not "features", instead things like capacity, security, load, performance, etc.

Test doubles are parts of tests that simulate some real part of the application. They are
- Dummies
- Fake objects
- Stubs
- Spies
- Mocks

INVEST principle for stories:
- independent,
- negotiable,
- valuable,
- estimable,
- small,
- testable
- [ ] Expand on this.

Involve QA when writing acceptance criteria to ensure that it's testable and properly defined.

Three times you can start adding tests:
1. New project: Do it and don't skip it. This is the best time to do it.
2. Midproject: Automate the most common happy paths. More manual testing. Automated any repeated tasks.
3. Legacy: Test the code you change. Consider if adding tests for the sake of it actually add any value.

When making proper integration tests, you test harness (copy of the system you have to integrate with, e.g. copy of API or similar) should be able to simulate anything that can possibly go wrong that's not under your control. Network outage, garbled responses, etc.

Close collaboration between testers and devs are is super important. Testers should make tests for all cases that devs are working against.

2 ways to manage defects (bugs)
1. Keep a bug backlog that should be empty at all times, i.e. zero tolerance for keeping bugs.
2. Treat bugs as features instead, i.e. they get prioritized and developed just like anything else.




The 5 step process for improving cycle time is:

1. Identify the constraint.
2. Exploit the constraint, i.e. set them up for success.
3. Subordinate others, i.e. force others to help out wherever possible.
4. Elevate the constraint, i.e. hire more people, add more compute power, etc.
5. Start from 1 again.
