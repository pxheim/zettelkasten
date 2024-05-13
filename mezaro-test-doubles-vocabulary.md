Mezaro's formal vocabulary of test doubles:

- **Dummies**: implementation of an interface that does nothing. Not terribly useful, but sometimes necessary.
- **Stubs**: implementation of an interface that returns something specific in order to be used in a test.
- **Spies**: same as stubs, but also remembers what was done and can be queried about it later. E.g. how many times was method x was called. Perhaps the most common test double.
- **Mocks**: same as spies, but also knows what to expect, i.e. test assertions are part of the mock. Basically you can see how many times method x was called with value y, and it'll fail if value z was provided instead.
- **Fakes**: Different from all the previous ones. These are fake implements some business rule that allow you to use it to test certain scenarios. E.g. for authentication it can return true for 'goodPassword' and false for 'badPassword'. Fakes are not used often. As application grows, so do fakes.
