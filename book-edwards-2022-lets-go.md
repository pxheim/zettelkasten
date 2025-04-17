[[$Bibliography]]

---

Some go concepts related to web applications.
- Handler: basically a controller. Responsibility is to execute application logic and writing HTTP response headers and bodies.
- Router (sevemux). Stores the mapping between the URL patterns and the corresponding handlers. Usually you have one servemux for the whole application.
- Web server that listens to incoming requests. In go, we can do this as part of the application itself. No need for Apache or Nginx.

