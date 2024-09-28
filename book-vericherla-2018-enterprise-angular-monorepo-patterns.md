An app is just the barebones code needed to imports libraries that can be used to build the application. At most this might contain some simple routing, and some 3rd party imports, typically sentry, mixpanel, etc.

A lib is where the logic for your application resides. There are a few different types of libs.

When generating an nx project, `tools` folder is where tooling resides, e.g. schematics.

