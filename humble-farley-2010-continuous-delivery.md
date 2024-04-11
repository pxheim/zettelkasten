Humble, J., & Farley, D. (2010). _Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation_. Addison-Wesley.

[[$Bibliography]]

[[deployment-pipeline]]




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

Testing is the responsibility of the whole team.

Rapid feedback is important for CI, but also in GTD. It must come asap, otherwise it's no longer relevant.

A typical deployment pipeline goes through the steps of commit, acceptance, performance, UAT and then production. In other words, devs commit & unit tests are run. If pass, acceptance tests are run, then performance / other automated tests, then we involve manual testers before prod release.

Never recreate binaries within the deployment pipeline. Build once and use the same binary throughout. Do not store these in VCS.

Use smoke tests (also called deployment tests) to test that your app is running after deployment.

The whole team owns a failed build. It's a team after all, and only as strong as it's weakest link.

The commit stage of a deployment pipeline is the first and should at a minimum compile (if needed), run unit tests and critical acceptance tests, create binaries for later and perform non-functional analysis, i.e. coverage, cyclomatic complexity, duplicate code, etc. Should not take more than 5 minutes.

Acceptance testing should test business cases, not technology. If it does, it can become costly and hard to maintain.

Testers should not just do regression tests when given a build. The should validate the acceptance tests, and do exploratory testing (that humans are good at). Good automates tests free up testers to do what they should.

When setting up a new pipeline, first make a skeleton (mock) of all the parts in your value chain, then automate deployment and build, then unit and component tests, then acceptance tests and finally releases.

Get metrics out of your pipeline. The most important is cycle time, i.e. time from feature idea to released to prod. Also measure each step in between. Secondary diagnostics include:
- Coverage
- Bugs reported
- Code metrics
- Velocity
- Duration og builds / tests
- Number of commits
- Number of builds
- Number of build failures
- Size

The 5 step process for improving cycle time is:
1. Identify the constraint.
2. Exploit the constraint, i.e. set them up for success.
3. Subordinate others, i.e. force others to help out wherever possible.
4. Elevate the constraint, i.e. hire more people, add more compute power, etc.
5. Start from 1 again.

The data collected must be visible to all parties involved, pref. "in your face". Good idea to visualize it.

All scripts & files needed for the whole deployment pipeline should be in VCS. One for commit stage, one for acceptance, and so on.

- [ ] Research Domain Driver Design.

Deploying regardless of to prod or beta or anything else should use the same deployment script. Config should be refactored out.

Always deploy your whole software from scratch.

Deployment script should leave env. the way it found it, i.e. deployment should be atomic. How can we do this with s3?

If part of a step in the pipeline fails, don't immediately fail the check. Perform all tasks, e.g. unit tests, integration tests, etc and then point out which failed / passed.

- [ ] "Integration hell", time reserved for integrating PRs. Must be done to integrate often. Should be done in time for builds to pass before eod. 

Set up the role of the "build master", which will oversee the status of the build. Usefor to establish good discipline. Role should rotate. Poke people who break the build and get them to fix / revert.

- [ ] James Carr & TDD - read.

An efficient commit stage should take no more than 5 minutes. Do not have any async tests as they are slow. Do not have tests with state. Do not test UI.

A good way of thinking about unit vs acceptance is that unit tests verify that the program does what the developer expects whereas acceptance verifies that it does what the customer wants.

If application is designed w/ smart / dumb components, then when doing acceptance testing, we are only interested in the smart components, thus we can forget about the dumb UI layer. This is good! We do not want to test UI unless we absolutely have to.

Iterative deployment process:
	1. Analyst, tester & customer work closely to defined and refine acceptance criteria.
	2. Analyst, tester & dev agree on acceptance criteria to test. This way, testers know what to expect.
	3. Dev makes feature & consults w/ analyst if anything is unclear.
	4. Analyst, tester & dev sit together while dev demos the finished feature. Small issues are fixed.
	5. Tester do the testing.

A kickoff ensures a shared understanding, prevents ivory tower analyst, testers wont raise defects that are unrelated, devs won't make stuff nobody wants.

> Acceptance tests are not just tests, they are executable specifications of the behavior of the program.

Acceptance tests should be written
- GIVEN (some initial context)
- WHEN (an even occurs (by some user))
- THEN (there are some outcomes)

If you have to interact w/ UI for acceptance tests, implement window drivers for the parts you have to deal with. Instead of acting on buttons directly from your tests, go through the window layer instead.

Same applies to application interaction. Make a driver.

Keep state in acceptance tests to a minimum. do not dump state to init a series of tests. INstead use the application to get to the state you want.

Tests must be atomic, i.e. they leave no traces of ever being run. This is why they can run in parallell == faster.

Making code testable = have to change how you write it. However, do not create "backdoors" that exposes things to be tested. If you have to do this, it usually is indicative of poor code design. (Example using the analysis package and private members).

Automated acceptance testing of external systems (e.g. API) is complicated. If you stub them you have full control, but then you do not actually integrate. Solution is to do both:
1. Have a small suite of integration tests that test the actual external system.
2. Stub the rest that you test.

- [ ] Idea: team huddle as soon as the build fails? It's painful as it should be, but perhaps effective? What seems to work best is something fun, but at the same time serious.

It is the responsibility of the whole team to keep the acceptance tests fresh.

Programmers love to refactor and optimize code, but most often they will do so for code that might not yield any benefit. Be strict and identify critical code before working on it. Donald Knuth: 97% time, premature optimization is the root of all evil. However, do not forget about the 3%.

Capacity testing should test scenarios, not external systems in isolation. A good strategy will be to convert some acceptance tests to capacity tests.

Avoid capacity testing through the UI, despite most common. Makes tests brittle and slow.

Tests should be fast. Unit tests very fast, acceptance tests as fast as they can be. Benchmark the tests & fail if they are taking too long.

Anybody should be able to deploy any version to any (maybe not prod) environment w/ click of a button. Developers should never do the release.

Blue-Green deployment: deploying to a copy of production, say green, while another is active, say blue. When time to update switch routing to green.

Canary releasing: release to prod a new version but only to a small set of users. Get feedback fast.

Cont. deployment to production, i.e. every change that passes all tests will get automatically released to production. Might be a dream state for most, but you should strive to code like your code would be auto released.

Not giving the users an option of whether they want to upgrade their system or not is most often the best idea. Automatic updates should be opt-out.

Crash reporting is an invaluable metric when doing CI/CD.

For ops / QA to be able to able to take over the deployment, they should be involved in making the deployment process.

When deploying, do not delete old files. Move them  / keep a copy of them.

- [ ] Look into symlinks for s3 maybe?

Keep bus factor low, everybody should be able to perform a deployment.

Deployment scripts should include tests to verify that the deployment was a success. These are smoke tests.