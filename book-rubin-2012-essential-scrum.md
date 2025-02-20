[[$Bibliography]]

On the cynefin chart, SCRUM only works when you are working in the complicated domain, which is what programming is.

---

Scrum roles consist of:

- Product owner, decides what should be made & when. Prioritizes everything. This includes technical work.
- Scrum master, helps make work flow in an agile way. Removes blockers.
- Dev team does the dev work. Must be cross functional & self organizing.

---

Do not focus each sprint on only one type of work. This is basically waterfall, but disguised as scrum. Each sprint should produce a deliverable artifact.

Manufacturing is different from software dev. One wants to make many of one thing, vs. wanting to make on thing many ways.

Wait as long as possible before making a decision about something. Wait until LRM (last responsible moment), when cost of not making a decision is greater than making it.

Plan as little as possible to get started. You know the least up front.

Assumptions are terrible. Validate them fast. Follow that fast feedback is key.

Focus on idle work, not idle workers. Don't enforce 100% utilization. Due to queueing theory, this is a bad idea. Also the focus should be on the baton, not the runners in the relay race analogy.

Only assets delivered to a customer have actual value. Any artifact produced along the way is waste.

---

Sprints should have goals that, as a rule, should never change. This is a contract between business & devs of what will be completed.

Definition of done should have a checklist to ensure that goal / feature is actually done.

---

Define "users" for your user stories, e.g. Tom can be an ops power user, "Bjarne" a developer, etc.

Common terminology includes

- Epics: span many months / releases.
- Features: span several sprints.
- Stories: span a few days or less.

Other related terminology:

- Tasks: things that need to be done in order to get the story done.
- Themes: collection of stories.

---

New features and changes should most often be written as stories. Bugs, refactoring and spikes don't have to.

Rule of thumb, have about 2 extra sprints worth of items ready to go.

Consider adding a definition of ready to stories that are in the backlog.

---

Use relative sizes for estimating. We are terrible at estimating absolute sizes.

Use different units for different things where appropriate, e.g. t-shirt sizes for features & story points for stories.

Avoid using ideal-days / hours. These are very often misunderstood.

Measure velocity as a range. Better for forecasting.

Velocity is a planning tool and should be used as that only. Do not strive for higher velocity or compare between teams. Leads to inflation of story points.

Velocity increases over time, but not linearly, and will eventually plateau. changes to team, or even acquiring new skills will make it dip, but should recover.

---

A strong definition of done helps prevent accruing technical debt.

Repay tech-debt incrementally. Just like how dieting does not work if you don't for a week, you should not have refactoring sprints.

Make the debt visible! Either track them as stories or have a dedicated backlog. PO odes not see the debt as clearly as developers.

---

Before spring, PO should ask themselves whether they would write a check to pay for the features being made.

PO must specify acceptance criteria before an item is estimated / considered by the dev team. Verify these during the spring to catch potential issues early. Most havs CD for this to work. Also important to ensure DoD before review.

PO can be PO for multiple teams, but never PO and ScrumMaster at the same time.

---

dev team members should not be Scrum Master, but _can_ if they really need to.

Scrum master for multiple teams is OK.

---

Do not move testing out into a separate team!

Dev team should spend ~10% of time grooming the backlog. Mostly assisting PO.

Form a team w/ T shaped skills, i.e. they know a lot about their speciality, but they also know a fair bit about other stuff, so they can help out there.

Specialists can be moved around, but dangerous as it interferes with team dynamics.

Teams are valuable due to their history of working together, team != group. Do not split teams or move people around if it can be avoided.

---

Component teams, usually specialists, can work, but only if there's a few products. Cross functional is better.

---

Be ware of performance review (annually) as they may foster intra-team competition. Provide team feedback every sprint instead.

---

Never plan more than you have to. A detailed long-term plan might misguide you from how things actually are.

**Limit waste. Ever time something is made or done that is wasteful, mark it as figure out why it happened. Don't do it again / remove process that caused it.**

Don't deceive yourself into thinking that just because you planned 10 months ahead that you'll actually be done then. However, planning is often done to answer just this; when will I be done.

Small iterative releases is like investing early. You make x$ every day. If you invest them every day, you'll make more money vs someone who invests all of their money at the end of the month. Compounding is real.

---

Work on weighted shortest job first. This is cost of delay / duration (effort).

Avoid just doing high profit work first, w/o factoring in the cost of delay.

Avoid planing out what you're going to work on for the next year. Typically this is done at some strategy gathering.

Do not allow large items into the portfolio backlog. Break them down first. > 9 months or so is a good benchmark.

Avoid common pattern of 1. start work w/ whatever is at the top of the backlog. 2. if done, repeat step 1. This causes a lot of idle work which is more dangerous than idle workers.

---

Be very wary of making assumptions based on what you "think" customers want. Pay for validated learning every time.

Don't fund all stages of a product at once. Do it in increments. Evaluate based on marginal economics before continuing.

---

When release planning you have 3 main variables: date, scope and budget.

- All fixed: don't do this. This is waterfall-ish.
- Fixed scope & date: Also bad. Flexible budget does not really work. Adding more people will just slow down the project. Date & scope will "play chicken".
- Fixed scope: Avoid, try to break down into smaller chunks.
- Fixed date: The best if scope really isn't fixed. Prioritize well & keep releasing.

Overly constraining date, scope & budget will come at the expense of quality, either technical or customer satisfaction.

Aim for around 60-70% of MRFs to be required. The rest are nice to have