What makes acceptance tests so important is that they are not just tests that verify that your application does what the customer wants, they are also executable specifications of the behavior of the program.

When just referring to acceptance tests, we most often mean functional acceptance tests. This is different from [[nonfunctional-acceptance-tests]].

Acceptance tests should be written in the form.
- GIVEN (some initial context)
- WHEN (an even occurs (by some user))
- THEN (there are some outcomes)

[[book-martin-2021-clean-craftsmanship]] advocates that acceptance tests should be written by QA (or business analysts) and then completed by the developers. The crucial part of this is that the tests will be written by business people and therefore be understood by them.

Avoid testing the UI wherever possible. It's slow and prone to error if the UI changes. If you need to test the user interface, all replies to it should be stubbed.