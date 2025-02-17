Focus on capabilities instead of maturity models. Maturity models are often set up in levels which you have to meed. Does not take into account ever-changing software. You can focus on the "right" capabilities for now. Each capability is tied to a specific outcome. Compare w/ CD book w/ maturity model. Break into capabilities.

---

Metrics that _do not_ affect performance

- Age and tech used.
- Whether ops or devs perform deployment
- Having a change approval board.

Four main ways to measure performance:

- Delivery lead time: Request --> Feature.
- Deployment frequency.
- Time to restore service. Delta time to fix a broken system/
- Change fail rate. How many # of changes result in failure.

Loosely put we can measure _performance_ through lead time & deployment frequency, _stability_ through time to restore, and _quality_ through change fail rate.

Research shows that increase in performance does _not_ negatively impact stability or quality, actually the opposite.

---

Three main types of culture

- Pathological (power oriented)
- Bureaucratic (rule oriented)
- Generative (performance oriented)

Good culture impacts both software delivery performance and organizational performance as well as lead to higher job satisfaction.

"Human error" should never be the result of a post mortem investigation. How teams interact is more important than who's on the team when it comes to making efficient teams.

Lean: Change how people behave, not how people think.

---

5 key principles for CD

- Build quality in: eliminate need for inspection by building quality into the procut. Deming.
- Work in small batches: at the expense of some overhead, releaeing to prod often.
- Automate everything: People solve problems, automate everything else.
- Always improve.
- Everything is a team effort.

To achieve TD you must have

- Comprehensive config management; set up & tear down everythign in VCS quickly for testing and deployment.
- CI
- CI, continuous testing. Devs should automate, QA should explore.

CD affects team burnout and decreases deployment pain (along with other benefits) as it becomes part of deaily work, nothing special.

Keep config, not just application code, in VCS ==> software performance.

Trunk based development > all. GitHub Flow works for open source, but that's it. You can have branches that are merged daily or more often, but never less often.

---

