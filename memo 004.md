---
publishAt: "2023-10-06"
ctime: 2023-10-06
title: "javascript get the caret position in a textarea"
---

To get get the caret position (not pixels) in a textarea, you can use this:

```js
element.selectionStart;
```

For example:

```html
<textarea>
	Fake it till make it.
</textarea>
```

```js
const element = document.querySelector('textarea')
const caretAt = element.selectionStart;
```

Here, the text in `<textarea>` is `Fake it till make it.` The caret was behind `it` . This should return `7` .