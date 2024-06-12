[[$Research]]

xss is on the rise, new record in 2024 most likely. Why?

Why is xss a problem? Because of SOP. JS can only access things of the same origin as defined by the ietf. 

Code injected into your page through XSS can access the same stuff as your own JS.

Browsers tried to protect from XSS. Filter was designed to be fast and not good, so it didn't work very well. It was then removed.

---

CSP - content security policy. Defines where you can load content from based on a header.

Inline styles will not work when csp is set. Same for inline js, eval, setInterval, etc. So this needs to be refactored. Inline styles might not be such a big issue to enable, but should be avoided.

Can greenlight certain inline coding using hash of the code.

---

`report-uri` can be added, which will be called w/ post request when csp fails for some reason. This is great to find xss or if marketing adds something new w/o your consent. Use for reporting only in the beginning to get data, then enable csp.

---

trusted types prevents your from using innerHTML. Only available for chrome based browsers for now.

---

SRI. Add hash to cdn loading to verify that whatever you are loading is the real thing.

Or just don't use cdn.

---

Cookie hijacking. Protect them. Cookies have secure flag to prevent them from being sent over anything other than https.

httponly flag protects javascript from seeing cookies. There's no good reason for js to see the cookies.

Cookie prefixes `__Host` or `__Secure` new ways of protecting cookies.

---

Storing token is local storage is a real threat if you have XSS. BFF pattern is better.

---

Force browser to use secure connection. HSTS. Must be enabled.

---

CSRF, cross site request forging. Prevented by same site cookies. Prevents sending your cookies to a site when redirected, e.g. when google search navigating to your page.

---

Clickjacking. Application can be loaded in an iframe that's on another site. x-frame options http leader. You can deny (or only same origin) loading application from iframe.

Alternative is `frame-ancestors` directive of CSP.

---

Data leak vie Referrer. Most of the time you do not need the referrer, so it's pretty safe to set it to `no-referrer`. Marketting might want it.

---

Feature policy, you can define whether camera, geolocation, etc. can be used. Somewhat deprecated.

Permissions policy is the new one, but it's only supported in some browsers.

Document policy might replace this in the future.

---

COEP, COOP, CORP [[$Research]].

---

Clear site data header. E.g. instruct the browser to clear cookies or storage. Crome supports some additional options.

---

WebAuth specification is coming. 
