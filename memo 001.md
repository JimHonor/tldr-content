---
publishAt: 2023-10-05
ctime: 2023-10-05
title: write text to clipboard in javascript
---

To write text to the clipboard, you can use this:

```js
navigator.clipboard.writeText(text)
```

Here, the text arg is the string to be written to the clipboard.

For example:

```js
navigator.clipboard.writeText("Hello world.")
```

Source: https://developer.mozilla.org/en-US/docs/Web/API/Clipboard/writeText