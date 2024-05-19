Hide features or functionality in your application behind some flag that can be turned on or off. This is a good strategy to be able to integrate unfinished code when doing CI/CD.

One very powerful use of feature flags comes when setting it up using firebase remote config. This way, someone can turn on or off the feature flag and the applications will update in real time. See [[blog-ordine-2023-feature-flags-setup-in-flutter-with-firebase-remote-config]]
