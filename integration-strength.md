Integration strength is defined as a new methodology to explain coupling between modules where structured design and connascence fall short. It defines four key couplings:

1. Intrusive coupling: when a module communicates through, and therefore depends on, the implementation details of another module. This is in contrast to using a public interface exposed by the module.
2. Functional coupling: when two modules are coupled by their functionality. There are several variation on this:
	1. Sequential functionality: when certain things have to happen in a specific order.
	2. Transactional functionality: when several operations all need to succeed for the whole transaction to succeed.
	3. Symmetric functionality: when two modules implement the same functionality. It's important to note that this does not have to be the same code. It's basically DRY as it was intended to be.
3. Model coupling: when two modules share the same model. Reusing the same model across multiple modules can be detrimental to modular design.
4. Contract coupling: when two modules are connected through a contract, an integration specific model. This fixes model coupling by using a contract instead that converts implementation details to primitives. Alternatively this can be a public method exposes an interface that will internally call private methods with proper strong typing.

While contract coupling is the "best", it's not a requirement for good design.

Links:

- [[connascence]]
- [[structured-design]]