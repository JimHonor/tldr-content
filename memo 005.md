---
ctime: 2023-10-29
publishAt: "2023-10-06"
title: "javascript how to get current url"
---

To get the full current URL, you can use the `window.location.href` property:

```js
window.location.href
```

Here, the `window.location` property return an object. It has a bunch of useful properties if you need some information about the current location of the document.

For example, if the current URL is:

```txt
https://developer.mozilla.org/en-US/search?q=location
```

These are all the properties that `window.location` gives us:

```json {2}
{
  "href": "https://developer.mozilla.org/en-US/search?q=location",
  "origin": "https://developer.mozilla.org",
  "protocol": "https:",
  "host": "developer.mozilla.org",
  "hostname": "developer.mozilla.org",
  "port": "",
  "pathname": "/en-US/search",
  "search": "?q=location",
  "hash": ""
}
```

See it? The value of `window.location.href` property is exactly the current URL.

reference:
- https://developer.mozilla.org/en-US/docs/Web/API/Window/location
- https://developer.mozilla.org/en-US/docs/Web/API/Location