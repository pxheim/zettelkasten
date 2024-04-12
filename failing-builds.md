When a build fails, which is inevitable, it's important that it's  the whole team that owns the failure and is responsible for getting the build back to green again. It might be a single person that broke the build, and this person will most likely try to fix it, but the team as a whole bears the responsibility of what to do about it.

When a build fails, this becomes the #1 priority of the whole team, but it can be a good idea to set up the role of a [[build-master]] to facilitate.

It's also important to highlight that the build has failed in a very clear way. Humble and Farley has found that something fun works best, but it's important to at the same time to keep it serious. An idea can be team huddle as soon as the build fails. It's painful as it should be, but also effective in getting everyone together to assess the issue.

In the end it's important to never go home on a broken build. You should always fix it, or revert the change that broke the build. It's also a good idea to limit how long someone is allowed to work on fixing the build before it's reverted.







If part of a step in the pipeline fails, don't immediately fail the check. Perform all tasks, e.g. unit tests, integration tests, etc and then point out which failed / passed.

Never go home on a broken build. Fix it or revert it. Set a time limit for how long someone is allowed to try to fix their build before reverting. Consider failing builds on things like styleguide issues, warnings, builds taking too long, tests taking too long, etc.