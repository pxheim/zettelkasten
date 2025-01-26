Skelton, M., & Pais, M. (2019). _Team Topologies: Organizing Business and Technology Teams for Fast Flow_. IT Revolution Press.

[[$Bibliography]]

For organizations that create systems, they are inevitably going to create systems that are copies of the communication structure - Conway's Law.

ORg. charts try to limit communications to "up" or "down" in an organization. However, people don't communicate like that. To achieve our goals, we talk to whoever we want to. Org. charts are not going to give us the actual structure of communication. Static org. design does not work. Needs to be able to adapt to changes.

Reverse Conway's Law => Designing a team based on what software architecture you want.

Reverse or not, takeaway is that designing and team communications are linked.

Dan Pink => Three elements of intrinsic motivation: autonomy, mastery and purpose.

High cognitive load is bad Consider it when decided on team size. Linked to intrinsic motivation.

Main obstacles to flow: Pushing against Conway's law, software too big for teams, confusing org. design options, context switching, reorgs, flow blocked, surprises and disengaged teams.

Teams organized in silos are less likely yo design systems that work effectively from end to end.

Use Conway's law to change org. structure / communications to suit the architecture you want.

Given that Conway's law holds true, org design directly influences system architecture , thus, indirectly whoever decides on the org. structure will decide the architecture. It them follows that these people need to be of a technical nature for success.

If teams are communicating even though they do not need to based on how the system should be architected, make them stop. Move them.

Many to many communication is bad and tends to produce monoliths. Typically happens if everyone needs to bee everything, and everyone needs to be in every meeting.

Research at Google shows that it does not matter who is on a team, but instead how that team functions. Speaking of performance.

Teams should never be larger than 7-9 people. This is due to Dunbar's number that sets a limit for how many people you can trust intimately. Dysfunction of a team is lack of trust, so do not go above this number. Often called "two pizza team".

Each part of the system should be owned by one team only. They will then be aware of short term changes and the mess they will have to clean later. This should not be territorial.

3 Types of cognitive load:
- Intrinsic: the core of the work you do, i.e. your basic skills, programming language, etc.
- Extraneous: Related to the env. in which you work. Instead of  "making" which is intrinsic, this is related to what you do with what you have made, deployment, config, etc.
- Germane: Aspects that need special attention. Where the value lies.

Remove as much as possible from intrinsic (through training, organizing, etc), and extraneous (by automating, etc) to allow people to focus on the germane.

Limit number of domain responsibilities per team. 3 types of domains:
- Simple: Most work has a clear path of action.
- Complicated: cHange need a few tries to get it right. Not always clear.
- Complex: Solutions are not clear. Experimentation and discovery is necessary.

A few guidelines on teams and domains
- Give each domain to a single team. If not possible, split the domain.
- A team can handle 2-3 simple domains.
- A team given a complex domain should not have any more domains.
- A team should only have one complicated domain (but can handle a simple one).

Team API is the way a team communicates w/ other teams, but also inside of itself. It's important that this is aligned and standards are set.

Arrange offices in the way you want your team to work. Only cubicles & only open space seldom works. Consider your team, and then how the office space should be.

Two main team anti-patterns
- Letting teams evolve on their own.
- Moving team members around often. Teams work best when they get to work with the same people over a longer period of time.

Team structures are not static. Design for change. Don't blindly adopt a model that work for someone and think it'll work for you (e.g. Spotify model).

The success of any given topology does not solely depend on the members of that team. but also the surrounding teams, support, etc.

There's no "right" topology for you, but there are several bad ones. Selecting your structure must be deliberate.

If engineering maturity is lacking, temporary teams can be beneficial, but ensure that they remain temporary. E.g. devops team might help you get started, but might become a bottleneck if left to stay.

Keep dependencies between teams to a minimum. Track dependencies and do not let them grow. This leads to wait times.

There are only four types of topologies you need to know about:
- Stream aligned team.
- Enabling team.
- Complicated-subsystem team.
- Platform team.

A stream aligned team is focused on one valuable stream of work which can be a single product, feature, user story, etc.

All other topologies exist to reduce the amount of load on the stream aligned team.

Stream aligned teams should include members that are capable of performing all actions needed to get the work flowing. I.e. there should be zero need for handoff & each member must likely perform more than one task.

Enabling teams help stream aligned teams stay up to date on tech, best practices, frameworks, etc. They should  never be dependent on each other, but should assist for a while until stream-aligned team becomes autonomous. 

Complicated subsystem teams work of (often) small parts of software that require almost exlusovely specialist knowledge. This can be things like mathematical algorithms, codecs, drivers, etc. Delivery should be fast and integration w/ stream aligned teams is important.

Platform teams ensure that the platform needed by stream algined teams to work autonomously is in place. This includes self service APIs, tools, services, knowledge and support.

If a platform is large enough, managing it can incolce all of the other team types as well as another platform team for the platform itself.

Avoid creating silos, e.g. QA department, UX team, etc. This ties into avoiding needing handoffs that ultimately create bottlenecks.

Simplest form of a platform is a few wiki pages underlining components and services used by the team. No need for a team when this is the case obv. TVP = thinnest viable platform is what you want.

Treat that platfrm like any other product that's made, nodt just as a collection of stuff made for developers.

Most teams should be stream-aligned. Try to convert teams that are not, e.g.
- Infrastructure to platform.
- Component teams to platform / other.
- Tooling teams to enabling / platform.
- Support teams should be stream aligned.
- Architects to part-time enabling teams.

Monoliths is architecture where all parts are tightly coupled. This is bad. They are often hard to spot:
- Application monoliths are single large apps with many dependencies.
- "Joined at the DB" usually happens when there's a massive DB that all apps view as the only source of truth.
- Monolithic builds - when you have to build everything just to release a part.
- Monolithic releases: When all small components can be built independently, but need to be released together.
- Monolithic thinking: when you enforce a single way to do a thing that hampers innovation "one size fits all".
- Monolithic workplace: when believing that a single type of office will fit all teams.
- Monolithic model: When enforcing a single domain language.

