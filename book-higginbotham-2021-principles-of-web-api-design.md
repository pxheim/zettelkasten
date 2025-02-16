[[$Bibliography]]

Api design communicates in 3 distinct ways:

- Across network boundaries through which protocol is selected, e.g. HTTP, MQTT or AMPQ, etc.
- Internally to developers through documentation and DX.
- Externally to the users.

Most concepts of software design such as modularization, encapsulation, loose coupling and high cohesion also apply to API design.

All implementation details of an API is hidden behind the methods that are exposed. Have no idea how things work, only that they do.

Similar APIs should be grouped to ensure high modularization and cohesion.

Data models are not the same as resources. Models are made to be optimized from a query perspective whereas the resources are optimized for the consumer. Exposing the data model as an API resource leads to coupling of the two. Don't do this.

Resources are not object or domain models. Objects cano use a resource, but should not be tightly coupled.

DB has data model, API serves a resource and code uses an object. Do not link these.

---

Don't let frontend wait until backend completes their implementation. Start a design process first so that work can be done independently.

Designing a good API up-front will prevent implementation details from getting in the way as well as reduce coupling.

Don't leak internal implementation details in your APIs. This often happens if coding starts before API design.

API first design process has 5 steps

- Discover: Figure out what you need.
- Design: Make an initial API design.
- Prototype: Make a mock API to get feedback.

^ Move between these steps until you and stakeholders are satisfied (does not mean complete). Then

- Deliver: Actually code the API.
- Onboard: Make people use your API.

ADDR (Align Define Design Refine) process is an API first process to help make APIs. It consists of 4 phases w/ 7 steps.

Since an API most likely impacts everyone from business to tech to the customer, designing an API should therefore also involve the "whole company", or at least a multitude of representatives.

The first step in ADDR is to identify digital capabilities. This should be done through job stories, which highlight the jobs to be done. These are written as WHEN X, I WANT TO Y, SO I CAN Z.

Job stories are not user stories. They do not have the user in focus, instead focus on the outcome. You _can_ add the the user in the want & can step, but focus should still be on the when.

Keep stories focused. Additional details can be put under an additional details section of the story. This can be UI/UX details, or when implementation details leak into the story.

After finding digital capabilities, break them down into activities and activity steps
- Activity: Browse for books.
	- Step: List books
	- Step: Search for books
	- Step: View book details.

Good way to identify all activities and steps is to do an EventStorming session. This helps uncover any missing domain events, as well as establish a common vocabulary, etc. In general aligns everybody. [[$Research]].

To sumarize:
- Job stories -> Activities -> Activity steps.

---
Find the boundary of your API and avoid the common antipatterns

- Do not make an API that tries to do everything
- Don't overload concepts. A "book" API is probably too broad. "catalog" API that concerns itself w/ books is prob better.
- Don't maek helper APIs if it can be avoided.

Boundaries are often found during an EventStorming sessions where "nouns" shift. E.g. when going from "cart" something to "order" something, it might indicate a new boundary and thus possibly a new API.

---

Before writing code, make an API model. This is like a wireframe, but for APIs

When deciding which resource an operation should act upon, be careful not to leak implementation details. If resrouce name is the same as the dB record, it's a happy accident.

Evaluate API wtih a sequence diagram.

API model or profile breaks down each operation in the API, and forces you to think about it in more details before writing any code. Like a wireframe it includes

- Operation name: the name of the operation in lowerCamelCase e.g. listBooks.
- Description: more info about the operation
- Participants: who's going to use the operation. This is often identified user groups such as customer, technician, etc.
- Resources: what resources from the DB is required? In this case, books for sure, but prob also book author.
- Emitted events: any even that is emitted by the operation. This can be used by the system to trigger some action, or simply for analytics. E.g. "Books Listed". They should always be past tense.
- Operation Details" this is the technical details. What are request paramters? What is actually returned? Is it async? Is it safe?

Categorize operations into safe, idempotent or unsafe

- Safe: requests that do not alter state. Typically GET.
- Idempotent: same request can be made multiple times, but same result is guaranteed. Typically PUT & DELETE.
- Unsafe: makes changes to target resource, cannot be done multiple times w/ same result. Typically POST & PATCH.

Hypermedia controls allow consumpers of an API to "react" to responses from the server. There are 4 main types:

- Index: offers up a list of all available actions.
- Navigation: pagination links.
- Relationships: links to resources related to the one you are looking at,.
- Context driven: informs client what actions are avilable.

Context driven are interesting. E.g. an article can have a status, and some links, these can be rel: self, update and submit, indicating what actions can be performed.

When designing APIs, avoid actions where the state of a resource is changed by the client. E.g. to enable a metering point, don't PATCH or PUT the metering point w/ enabled: true, instead call POST to meters/{id}/enable.

Use GET/me instead of GET users{id} when you want to get your own user's information. This is called a singleton resource. Usually represented by a singular noun, e.g. users/{id}/config.

"Fire-and-follow-up" is a REST pattern where client sends a request tthat takes a while. Receives a 202 w/ Location URI in return. The location is an endpoint to a job where GET will return job status. When job status is complete, client can show this to the user.

---

RPC is good when speed is important and coupling is fine (server and client will be tightly coupled). Basically speed is traded for coupling.

In real time communication (async messaging), there are three main types of messages, request, response and event. The request and responses are linked, i.e. they can be sync or async.

Message broker sits between publisher of a message and the consumer(s). This is great! Publisher does not have to know about rest of system, queuing can be handled by the broker, distribution is easy, etc.

---

Biggest benefit of a microservice approach is to reduce cognitive load on devs & reduce the need to coordinate as much. Only works if

- DevOps is good, i.e. rapid onboarding due to most things being automated, well tested, easy to deploy, etc.
- Proper team structure, not handoffs to silos. "If you own it, you manage it".
- Remove centralized data-ownership.

Async microservices are almost always better than sync ones, even though they may initially be more complex. Con start or stop services w/o changing others. Brokers handle messages, avoid message chainign, etc.