Definition: A class should have only one reason to change, meaning it should have only one job or responsibility.

The SRP makes testing and maintaining the class much easier as a change in a requirement that affects one area of responsibility should only necessitate changes in one class.

[[smart-and-dumb-components]] is an example of this where there's one class (component) that handles data management and another to handle ui rendering.
