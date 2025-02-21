[[$Bibliography]]

Focus on capabilities instead of maturity models. Maturity models are often set up in levels which you have to meed. Does not take into account ever-changing software. You can focus on the "right" capabilities for now. Each capability is tied to a specific outcome. Compare w/ CD book w/ maturity model. Break into capabilities. The book concludes w/ 24 capabilities that you should strive towards.

---

Metrics that, contrary to popular belief, _do not_ affect performance

- Age and tech used.
- Whether ops team or dev team perform deployment.
- Having a change approval board.

There are four proven ways to measure performance.
- Delivery lead time: How long it takes before a request for a feature is actually completed.
- Deployment frequency: How often deployments to production are made.
- Mean Time to Restore: Average time it takes to recover the system from failure.
- Change fail rate: Percentage of code changes that lead to failure.

Loosely put we can measure _performance_ through delivery lead time & deployment frequency, _stability_ through time to MTTR, and _quality_ through change fail rate.

Interestingly, research shows that an increase in performance does _not_ negatively impact stability or quality, actually the opposite happens. Lower delivery lead time and faser deployment frequency positively impacts stability and quality.

---

Westrum defines three main types of cultures in companies that can be compared to software companies:

- Pathological (power oriented)
- Bureaucratic (rule oriented)
- Generative (performance oriented)

Good culture impacts both software delivery performance and organizational performance as well as lead to higher job satisfaction.

---

5 key principles for CD

- Build quality in: eliminate need for inspection by building quality into the product.
- Work in small batches: at the expense of some overhead, releasing to prod often.
- Automate everything: People should solve problems, automate everything else.
- Always improve, SCRUM comes to mind here.
- Everything is a team effort. Again people are in focus.

To achieve CD you must have:

- Comprehensive config management; set up & tear down everything in VCS quickly for testing and deployment.
- Continuous Integration (CI)
- Continuous testing. Devs should automate, QA should explore.

CD affects team burnout and decreases deployment pain (along with other benefits) as it becomes part of daily work, nothing special.

Trunk based development is a must for CD. GitHub Flow works for open source, but that's it. You can have branches that are merged daily or more often, but never less often.

---

System type does not impact delivery performance. E.g. using fancy new framework is not going to make things better. However,  two architectural characteristics that impact performance:

- No need for integrated env. when testing.
- Deploy / release w/o depending on other apps & services.

Architects should focus on the people, not tools & tech. Devs should be free to pick whichever tools is best suited for a task.

---

OWASP Top 10 [[$Research]]

Infosec should be build in and not an afterthought.

---

WIP limits do not alone have an impact on performance, only when coupled with publicly available information dashboards. This also impacts culture positively.

Having a CAB is worse than having no process at all, both for performance and stability.

Keep change approval lightweight. See [[pull-requests-and-continuous-integration-ship-show-ask]] Automate wherever possible. CI for tests.

---

Teams should be free to change requirements on their own w/o needing approval. Ofc. this only works if other good practices are also followed. Don't just let your devs free.

Lean drives software delivery performance, and good software delivery performance drives good lean practices.

---

The more painful deployments are, the poorer the IT performance, org. performance & org. culture.

To avoid burnout, focus on

- Respectful env. Don't blame for mistakes. See Westrum generative culture.
- Communicate strong sense of purpose.
- Invest in employee development.
- Fixing blockers.
- Give time, space and resources to learn.
- Must be given autonomy.

Don't fall into pitfall of fixing person vs. fixing the env.  Lean states that: "Change how people behave, not how people think". "Human error" should never be the result of a post mortem investigation. **How teams interact is more important than who's on the team when it comes to making efficient teams.**

Things that cause burnout

- Work overload.
- Lack of control.
- Insufficient rewards (salary, social, etc.)
- Unsupportive work env.
- Lack of fairness in decision making.
- Value conflicts, mismatch between individual & organizational values.

Fixing burnout, in order of importance:

- Organizational culture, strive towards a Westrum generative culture. This is the responsibility of managers.
- Deployment pain, often done outside of business hours. Fix the most painful first.
- Effectiveness of leaders, limit WIP & remove blockers.
- Org. investment in devops.
- Org. performance, give space to experiment and potentially fail during work hours.

---

Measure eNPS (employee net promoter score) to find loyal employees. Loyal employees perform better than not.

People who strongly identify w/ company they work for put out better work.

Diverse teams perform better, but only if they are also inclusive. Diversity includes both gender & underrepresented minorities.

---

Teams w/ strong transformational leaders perform well, but a transformational leader along does not generate amazing performance (you cannot polish a turd). They enable the teams to user lean and CD processes, but cannot do it for them.

Five characteristics of transformational leaders:

- Vision: clear understanding of 5 year plan.
- Inspirational communication: even in uncertain times.
- Intellectual stimulation: asks good questions.
- Supportive leadership: care and consideration for peeps.
- Personal recognition: praise and acknowledgement.

Managers have responsibility for people. Best case is when managers are also leaders.

Managers should make a training budget available and let devs know about it and let _them_ pick what they want to learn.

Set up yak-days to work on tech debt, or hack-days to work on a specific feature.

Give time after release to experiment.

Things leaders, managers or just normal engaged devs can do to improve culture:

- Building trust w/ other teams. This takes time!
- Encourage devs to move laterally between departments.
- Reward work that facilitates collaboration.
- Make it safe to fail.
- Set aside ~20% of time to experiment.
- Share info on "lighting talks" or luch & learn.

Set up monitoring!

Review ING chapters when relevant.