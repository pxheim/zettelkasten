[[$Bibliography]]

There are three main ways APIs will communicate their information
- Internally between programs through network boundaries such as HTTP, MQTT, AMPQ, etc.
- Internally to developers through documentation and developer experience.
- Externally to users of the API.

Most concepts that apply to writing good software will also apply to making good APIs, e.g. modularization, encapsulation, loose coupling and high cohesion.

All implementation details of an API is hidden behind the methods that are exposed, and it should stay that way. An API should never leak implementation details. If the resource an API is acting upon is the same as the DB record name, it's a happy accident.

Similar APIs should be grouped to ensure high modularization and cohesion.

Data models are not the same as resources. Models are made to be optimized from a query perspective whereas the resources are optimized for the consumer. Exposing the data model as an API resource leads to coupling of the two. Don't do this. Resources are not object or domain models. Objects cannot use a resource, but should not be tightly coupled.

DB has data model, API serves a resource and code uses an object. Do not link these.

---

When deciding to make a new API, avoid waterfall development. Start a design process that enables frontend and backend to work simultaneously and independently. Designing a good API up front before coding prevents implementation details from getting in the way, and should help reduce coupling. 

Don't leak internal implementation details in your APIs. This often happens if coding starts before API design.

"API-first" design process consist of 5 steps where you'll iterate between the first three for a while until you reach a point where you (and stakeholders) are satisfied.

- Discover: Figure out what you need.
- Design: Make an initial API design.
- Prototype: Make a mock API to get early feedback.
- Deliver: Actually code the API.
- Onboard: Tell users about the API.

The book outlines a process called ADDR (Align Define Design Refine) to design APIs this way. It consists of 4 phases w/ 7 steps. The first step in ADDR is to identify digital capabilities through something called Job Stories - similar to user stories - which highlight the job to be done. They are written as `WHEN X, I WANT TO Y, SO I CAN Z`. They differ from user stories in that they don't have the user in focus, instead they focus on the outcome. You can add the user in the `WANT` and `CAN` step, but the focus should still be on the `WHEN`. The stories should be focused one a single job, but additional details can be added to the story.

Job stories will help you discover the digital capabilities that your API should expose. When you have these, it's a good idea to break them down into activities and activity steps. E.g

- Activity: Browse for books.
	- Step: List books
	- Step: Search for books
	- Step: View book details.

To ensure that you've discovered all activities and steps, you can hold an EventStorming session which will help uncover any missing domain events as well as establish a common vocabulary to align everyone.

Since an API most likely impacts everyone from business to tech to the customer, designing an API should therefore also involve the "whole company", or at least a multitude of representatives.

---

Don't try to make an API that does everything. Identify the boundaries of the API you are trying to make. This can often be seen where the "nouns" found during an EventStorming session changes, e.g. when going from "cart" something to "order" something, it might indicate that there's a boundary here which might warrant a new API.

Avoid the common anti-patterns:
- Don't make an API that tries to do everything.
- Don't overload concepts. E.g. A "book" API is probably too broad and will try to do too much. A "catalog" API that concerns itself with books is probably better. 
- Don't make helper APIs if it can be avoided.

---

Before writing any code, make an API model. It's like a wireframe for APIs which break down each operation in the API and forces you to think about each one before writing any code. It includes:
- Operation name: the name of the operation to be performed, e.g. listBooks.
- Description: more information about the operation.
- Participants: who's going to use the operation. This if often a user group such as "customer", "technician" or "developer".
- Resources: what resources from the DB is required? For books it's obviously going to be books, but can also include book autor.
- Emitted events: this lists out any event that emitted by the operation that can be used internally in the system. E.g. listBooks will likely emit an event "Books Listed".
- Operation details: this is the technical part of the API, what request parameters are required / options, what is actually returned, is it safe*, etc.

APIs should be categorized into safe, idempotent or unsafe.
- Safe: state is not altered, typically a GET request. You can get a list of books many times and no state will ever be changed and you'll always get the same result.
- Idempotent: same request can be made many times and the same result can be guaranteed, typically PUT and DELETE requests. You can PUT a book to update its information (alter the state), but regardless of how many times you PUT with the same information, you'll always get the same result.
- Unsafe: requests that make changes to the target resources, and cannot be done multiple times with the same result, typically POST and PATCH. If you POST a new book multiple times, you're going to alter the state by creating a new book, and if you POST many times, you'll keep creating new books.












Evaluate API with a sequence diagram.


Hypermedia Controls (previously HATEOAS), allow consumers of the API to interact with responses from the server through links to other actions. There are 4 main types:
- Index: lists additional available actions.
- Navigation: pagination links.
- Relationships: links to other resources related to the one you are looking at.
- Context driven: Actions available on the resource for the given context.

Context driven is interesting. E.g. an article can have a status indicating whether it's a draft or a published article. Based on that an API that returns this article can have context actions to either update, publish or remove.

Example:

```
{
	[...]
	resource details
	[...]
	"_links": {
		"self": {
			"href": "articles/12345"
		},
		"update": {
			"href": "articles/12345/update",
			"method": "POST"
		}
		"delete": {
			"href": "articles/12345/delete"
			"method": "POST"
		}
	}
}
```

When designing APIs, avoid actions where the state of a resources is changed by the parameters sent to a PUT request, e.g. to enable a metering point, don't PUT to a metering point resource w/ enabled: true. Instead make a PUT call to meters/{id}/enable.

Create singleton resources for ones that are accessed often and that can improve DX. Most common example would be to make a singleton resource for `users/me` to list the currently logged in user instead of having to write `users/12345/config`. 

A useful REST pattern is the one called "fire-and-follow-up", which uses the Hypermedia controls in a smart way. When the client requests something that can take a while, it will make a request for this and get a 202 response w/ a location. This location is an endpoint the client can GET in order to get information about the status of the request. Until the request is completed, the status will be something like "processing". Once completed, however, the client can show the actual result to the user.

---

RPC is good when speed is important and coupling is fine (server and client will be tightly coupled). Basically speed is traded for coupling.

In real time communication (async messaging), there are three main types of messages, request, response and event. The request and responses are linked, i.e. they can be sync or async.

Message broker sits between publisher of a message and the consumer(s). This is great! Publisher does not have to know about rest of system, queuing can be handled by the broker, distribution is easy, etc.

---

Biggest benefit of a microservice approach is to reduce cognitive load on devs & reduce the need to coordinate as much. Only works if

- DevOps is good, i.e. rapid onboarding due to most things being automated, well tested, easy to deploy, etc.
- Proper team structure, not handoffs to silos. "If you own it, you manage it".
- Remove centralized data-ownership.

Async microservices are almost always better than sync ones, even though they may initially be more complex. Con start or stop services w/o changing others. Brokers handle messages, avoid message chaining, etc.

Three main microservice architecture styles:

- Direct service communication
- API based orchestration
- Cell based architecture

Companies will often start with 1, and then move to 2 or 3 when complexity increases. 3 is often called Domain-Oriented Microservice Architecture, or DOMA for short.

Microservices are dynamic and evolve over time. Splitting a service should be easy and should be done when service grows out of bounds. Focus on _purpose_, not the _size_.

Use Microservice Design Canvas (MDC) to evaluate whether a microservice does too much, or is fine the way it is.

Avoid splitting into one service per CRUD operation. Created too much coupling between the microservices.

You can "think smaller" without moving the entire organization to microservices. There are a lot of good concepts from microservices but you don't need to implement all of then. Remember YAGNI.

---

When designing an API, forget frameworks, languages, formats, etc. for a while. Consider first the consumer of the API, then everything else.

Always mock your APIs before they are finished. Helps uncover issues, better for CI/CD and can be used for tests later. Three types:

- Static resource: Fake hardcoded data is returned for requests.
- Prototype: full CRUD support, but made like a POC: Basically POC baskend for the API.
- README: Just write out in a readme what the API does. E.g. 1 request, 2 response and 3 response body. It's basically does.

---
 Don't rely on the APP being the only thing that tests the API. The app might not test all edge cases as they are performing client side validations.

Don't underestimate the amount of data sets needed in order to efficiently test APIs.

---

There are many different API description formats. Let's look at the most common ones.

- OpenAPI Specification (OAS) or Swagger. Probably the most common. Known for "try it out" button.
- API description blueprint. Uses markdown, so makes it easy to use and distribute.
- RAML, YAML based format
- JSON Schema: used to describe responses. Now supported by OAS
- APIs json: basically a sitemap for your API that's machine readable.

---

APIs are forever, so plan accordingly.

---

Rate limiting an API is good for preventing traffic spikes, but also from devs that potentially messed up.

