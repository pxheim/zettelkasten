Humble, J., & Farley, D. (2010). _Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation_. Addison-Wesley.

[[$Bibliography]]

[[deployment-pipeline]]

[[implementing-ci]]

[[ci-requires-a-change-of-mindset]]

Humble and Farley mention that discipline is extremely important for efficient CI. This contradicts setting up env. where you have to use little willpower.

[[automated-frequent-releases-for-quality-software]]

[[only-build-binaries-once]]

[[do-more-often-the-steps-in-a-process-that-hurt]]

[[happy-path]]

Configuration management is all about keeping your config files, e.g. package.json, env. pubspec, or similar in VCS so that they can be used to set up same env. when new person starts or you wish to check out an older version.

A good configuration management must
- Exactly reproduce any environment you have for your application.
- Allow incremental changes to any of your environments.
- See and track all changes done to any environment.
- Satisfy all compliance regulations.
- Make it easy for all team members to get all the information they need and make the changes they need to make.

Lock down versions, even minor ones, to ensure we always have the same dev. environment.

Checking in all your ext. libraries to VCS is prob not going to work, but good idea to keep a separate repo w/ the dependencies. App can then get the dependencies from there.

[[branching-is-bad-for-ci]]

CI only works w/ long commit messages describing what you did in detail. ALSO link to JIRA task or similar. This applies to our PRs more than commits in "our flow".

[[types-of-software-tests]]

[[universal-rules-for-software-tests]]

[[testing-quadrant]]

[[unit-tests]]

[[acceptance-tests]]

[[nonfunctional-acceptance-tests]]

Component tests test the behavior of several components in your application.

[[reporting-from-ci-must-be-visible]]

Always run at least some tests locally before committing. Ensures you don't break the build unnecessarily or waste CI resources.

Good test coverage is a requirement for CI, thus TDD is almost a must.

Self thought: PRs are generally anti-CI, but are a necessity. They MUST be kept small. Break down tasks & split PRs by using feature flags, abstractions, etc. Reserve time for deep focus on reviewing PRs.

Three main types of tests that are made by and for developers, unit, component and deployment tests.

[[smoke-tests]]

Business facing critique tests often involve testing or showcasing completed features to get feedback for changes.

Test doubles are parts of tests that simulate some real part of the application. They are
- Dummies
- Fake objects
- Stubs
- Spies
- Mocks

[[invest-principle-for-user-stories]]

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

[[when-a-build-fails]]

[[build-master-role]]

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

[[theory-of-constraints]]

The data collected must be visible to all parties involved, pref. "in your face". Good idea to visualize it.

All scripts & files needed for the whole deployment pipeline should be in VCS. One for commit stage, one for acceptance, and so on.

- [ ] Research Domain Driven Design.

Deploying regardless of to prod or beta or anything else should use the same deployment script. Config should be refactored out.

Always deploy your whole software from scratch.

Deployment script should leave env. the way it found it, i.e. deployment should be atomic. How can we do this with s3?

- [ ] "Integration hell", time reserved for integrating PRs. Must be done to integrate often. Should be done in time for builds to pass before eod. 

- [ ] James Carr & TDD - read.

An efficient commit stage should take no more than 5 minutes. Do not have any async tests as they are slow. Do not have tests with state. Do not test UI.



If application is designed w/ smart / dumb components, then when doing acceptance testing, we are only interested in the smart components, thus we can forget about the dumb UI layer. This is good! We do not want to test UI unless we absolutely have to.

Iterative deployment process:
	1. Analyst, tester & customer work closely to defined and refine acceptance criteria.
	2. Analyst, tester & dev agree on acceptance criteria to test. This way, testers know what to expect.
	3. Dev makes feature & consults w/ analyst if anything is unclear.
	4. Analyst, tester & dev sit together while dev demos the finished feature. Small issues are fixed.
	5. Tester do the testing.

A kickoff ensures a shared understanding, prevents ivory tower analyst, testers wont raise defects that are unrelated, devs won't make stuff nobody wants.

If you have to interact w/ UI for acceptance tests, implement window drivers for the parts you have to deal with. Instead of acting on buttons directly from your tests, go through the window layer instead.

Same applies to application interaction. Make a driver.

Keep state in acceptance tests to a minimum. do not dump state to init a series of tests. Instead use the application to get to the state you want.

Tests must be atomic, i.e. they leave no traces of ever being run. This is why they can run in parallell == faster.

Making code testable = have to change how you write it. However, do not create "backdoors" that exposes things to be tested. If you have to do this, it usually is indicative of poor code design. (Example using the analysis package and private members).

Automated acceptance testing of external systems (e.g. API) is complicated. If you stub them you have full control, but then you do not actually integrate. Solution is to do both:
1. Have a small suite of integration tests that test the actual external system.
2. Stub the rest that you test.

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

Law of Demeter: design guideline for OOP to prevent tightly coupled classses stating that for a method M of class C, M should only invoke methods of:
- C itself
- Object created by C
- Object passed as arg to M
- Object held in an instance variable of C
- A static field

Componentization is key to be able to release things continuously. Do componentization when a project is in its infancy. Terrible later.

3  main strategies for keeping your app releasable. Following all can enable a team to forgo branches completely in VCS.
1. Hide new functionality (feature flags).
2. Incremental releasable changes.
3. "Branching" by abstraction for larger changes.

Componentization is a 4th, but is only reserved for large scale applications.

Tempting to do big changes as it may seem easier to break app then then fix it again when changes are made. This is most often an illusion. You are better off breaking changes down and keeping the app releasable.

Branching by abstraction is a method where you replace a part of your code by first identifying the "seam", i.e. all entry points to this code. Then make an abstraction of the code you need to replace before implementing the abstraction. Then you can replace the code by making a new implementation of the abstracted interface.

Do not split teams up based on components. Do it instead on user stories. Then componentization become everybody's responsibility.

Keep one pipeline for your entire application if you can. Can get quite large before needing to split it up. There's always additional overhead associated with splitting up.

Potentially start integration as soon as unit tests pass (to save time).

Common to refresh dependencies after every release.

[[branching-is-bad-for-ci]]

When making release branch, grab binary from artifact repo and use it. Do not regenerate build.

Software that has not been released is the same as inventory in your warehouse. You spent money making it and you're not making money from it just sitting there.

Maturity model [[$Reference]]

Use the Demming cycle when working with the maturity model: plan, do, check, act.

Incremental improvements when implementing CI. Do not attempt to do it all at once.

1. Classify the current state.
2. Pick an area that is a pain-point.
3. Implement changes.
4. Retrospective.
5. Pick another option.

Project lifecycle steps:
1. Identification: Figure out the business case and determine stakeholders and other key people.
2. Inception: Gather requirements, scope features & analyze data w/ stakeholders from pt. 1. Loosely based on speculation. Don't be worried if things decided here will change.
3. Initiation: Agree on the "practical" stuff before you actually start work. Architecture, set up server, etc.
4. Develop and release: iteratively.
5. Operation: support release and develop new things following the procedure, starting from 1.

Risk management 101: On a scale from 0 to 1, determine the probability of something going wrong. Figure out cost if the risk materializes. These values multiplied will be your risk. Mitigate based on what has the highest risk, however discount force majeure things.

