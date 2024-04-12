Tests small pieces of your application in isolation from the rest of the application. Commonly these will test that a method, given an input, will return an output. They verify that the code does what the developer expects.

These are the fastes and cheapest tests to run, and should be included as one of the first steps in your [[deployment-pipeline]].

Unit tests should be structured in a way so that they have three distinct steps:
- PREPARE
- TRIGGER
- TEST
