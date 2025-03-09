Connascence is a way to describe how something is connected. E.g. connascence by name means that something is connected by name. This can be used to explain how software modules are connected. A module is said to have connascence of the highest type present.

We can split connascence into static and dynamic. The highest level of static connascence is lower than the lowest level of dynamic connascence. From low to high, static connascence:

- by name: a naming change somewhere results in a naming change being required somewhere else.
- by type: when two modules have to agree on using the same type.
- of meaning: when two modules attribute meaning to some arbitrary value. E.g. the same magic value is transmitted between two modules, and they need to share a common understanding of what this value means.
- of algorithm: when two modules have to agree on using the same algorithm or protocol to understand the values transmitted between them. E.g. two modules that have to agree on which type of encryption to use.
- by position: when the order of something matters, e.g. the order of input parameters.

and dynamic:

- of execution: when the execution of something needs to follow a specific order. E.g. first A, then B, then C.
- of timing: when execution needs  to have a specific interval between them.
- of value: when a change in a value requires a change in another for the system to exist in a valid state.
- of identity: when two objects are dependent on the exact instance of a third object. The example often used here is two classes that operate on the same data in a shared database.

Links:

- [[structured-design]]
- [[module-integration-strength]]
