# Integration Guide

InspireMint can be embedded as a widget inside another webpage using an `<iframe>` or by including its files directly.

## Option 1: Iframe Embed

The simplest approach — drop an iframe into your page:

```html
<iframe
    src="path/to/InspireMint/index.html"
    width="100%"
    height="500"
    style="border: none; border-radius: 16px;"
    title="InspireMint Quote Widget"
></iframe>
```

## Option 2: Direct File Include

Copy the following into your project:

```
/data/*.json
/src/*.js
styles.css
script.js
assets/logo.svg
```

Then paste the relevant HTML from `index.html` into your page and link the CSS/JS:

```html
<link rel="stylesheet" href="path/to/styles.css" />
<script type="module" src="path/to/script.js"></script>
```

### Adjusting Paths

If your directory structure differs, update the `fetch()` paths in `src/quote-engine.js`:

```js
const res = await fetch(`your/custom/path/${cat}.json`);
```

## Option 3: Single Quote API (Advanced)

You can import the quote engine directly in your own JS:

```js
import { loadQuotes, getRandomQuote } from "./src/quote-engine.js";

await loadQuotes();
const quote = getRandomQuote({ category: "success" });
console.log(quote.text, "—", quote.author);
```

This lets you render quotes however you like without using InspireMint's UI.

## Notes

- InspireMint uses ES Modules (`type="module"`), so it must be served over HTTP (not `file://` protocol) for the `fetch()` calls to work in all browsers.
- A simple local server works: `npx serve .` or `python3 -m http.server`.
