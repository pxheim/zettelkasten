Definition: Reduce the coupling between different parts of a system by relying on abstractions rather than concrete implementations.

This often comes into play for data management when you have a class depending on some external service, say Analytics. Instead of a `AnalyticsManager` class directly instantiating `GoogleAnalytics`, it should instead depend on an `Analytics` interface. This way we can swap out `GoogleAnalytics` for, say `Mixpanel` without changing the `AnalyticsManager` class.
