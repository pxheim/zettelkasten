The words "module" and "component" are often used interchangeable to mean the same thing. To avoid confusion, we define module as "a boundary encompassing a well defined functionality exposed to the system". A module can be a class, a service, a method, or whatever, as long as it meets this definition.

A module can be broken down into:

- Function: it's public API that is exposed to the rest of the system.
- Logic: it's internal implementation.
- Context: it's dependency on execution environment.

A module should have high cohesion, which means that the content inside the module should be tightly coupled. If not, it's likely a sign that the module should be split.

Links:

- [[modular-design]]