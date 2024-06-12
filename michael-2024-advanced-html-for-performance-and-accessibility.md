[[$Research]]

Don't fall into the trap of thinking that just because html is simple, it's also not important.

Using the correct tags in html is equivalent to specifying types in ts. If you just use the `any` type everywhere, it's like using `div` everywhere. Don't do this. It breaks the accessibility tree.

It's easy to forget the amount of nodes each component consist of and the fact that it actually needs to be rendered.

Use heading elements in order. It's used for a11y. If you keep using the same element, you break this way of navigating.

You might not need a date picker. [[$Research]]

`popover` and `dialog` are great, but not supported just yet.

Buttons might not look the way you want. Don't be tempted to use a div, it breaks a11y and more. Instead use a CSS reset to make the button look like the div.

If you are writing css or js that conveys information, ask yourself if that's also available in the a11y tree. If not, maybe add some aria.

---

Set a width and height for your image. Helps with the Cumulative Layout Shift (how much elements jump around when something loads).

`img` tag supports a lot of things to help performance. `srcset` and `sizes`.

html has lazy loading of images and iframes. Just add `loading="lazy"`.  Sometimes you have to add width and height for browsers to allow this. Again because of the cumulative layout shift.

However! We only want to lazy load images that are not in the viewport when the page loads. This affects LCP (largest contentful paint).

---

HTTP 1 - multiple connections, multiple responses.

HTTP 2/3 - one connection, multiple responses. Responses need to be prioritized and are different between browsers.

We fix this with `fetchpriority` hints: high, low and auto. These are kinda more like suggestions vs hard requirements. What the browser does is not well documented. The priority is mostly relative.

---

Resource hints: preconnect and dns-prefetch. These are used on the rel property of the link tag.

preconnect is for critical connection. Don't use it for everything.

---

Preloading resources. Most used, but maybe most misunderstood? Link rel, same as before.

Prepares resources you don't need now, but that you're going to need later.

Only preload critical things. Don't use it everywhere. Be careful, it can actually impede performance if used wrong. What is wrong?

Fonts and images are good candidates in css. 

---

103 Early hints? new HTTP code. [[$Research]].







