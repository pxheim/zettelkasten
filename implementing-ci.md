If you want to implement CI, it first requires a change in mindset by the people who are willing to do it. [[ci-requires-a-change-of-mindset]].

You do not have to automate everything at once. Incrementally is fine, but it's good to keep in mind that almost everything can and should be automated in the end.

CI requires at minimum three things:
1. Everything must be in VSC.
2. One click build & test from CLI.
3. Team must agree on doing it.

Despite every team, software and company being different, there are 7 steps that will almost always be part of a CI workflow:
1. Wait for current build to succeed.
2. Update your code /w origin.
3. Ensure local code runs w/ changes.
4. Commit your changes.
5. Wait for CI to check your changes.
	1. Fail: Fix and go to step 3
	2. Pass: Rejoice!

Automated acceptance tests can be costly to maintain, and can create quite the overhead. A good middle ground is to make automated [[acceptance-tests]] for all [[happy-path]] mixed with 80% [[unit-tests]] coverage and some acceptance tests for the most important flows. This is the best starting point.