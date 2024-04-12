The Deployment Pipeline is the process that takes your application from code to release. What this pipeline is going to entail will vary greatly from company to company or even app to app. Most commonly you will have various stages that the application needs to pass through on its way towards being released. These are sometimes referred to as gates.

A typical deployment pipeline goes through the steps of:
- Commit: Developers commit their changes and [[unit-tests]] are run.
- Acceptance: [[acceptance-tests]] are run.
- Performance: [[nonfunctional-acceptance-tests]] are run.
- UAT: manual testing is done by QA.
- Release: production release.

