Structured Design is a methodology used to identify coupling between modules. It's largely outdated, but it has served as a building block for better methodologies.

It defines 6 different types of coupling, ranging from high(bad) to low(good):

1. Content coupling: when one class uses the data directly from another class. The are coupled through their content.
2. Common coupling: classes are coupled through the use of a global (common) state.
3. External coupling: classes are coupled through the use of an external state. Basically the same as #2, just that the state is not global.
4. Control coupling: classes are coupled by their implementation details. E.g. a method exposes how another method is to be executed.
5. Stamp coupling: classes are coupled by shared data structure. E.g. a method exposing the Customer data structure through getCustomer instead of a primitive through getStatus.
6. Data coupling: classes are barely coupled and integrate only by sharing as little information as possible, and only through explicitly defined interfaces (contracts).

Links:

- [[connascence]]
- [[integration-strength]]