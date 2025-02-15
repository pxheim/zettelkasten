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

