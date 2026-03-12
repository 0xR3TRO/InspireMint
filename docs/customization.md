# Customization Guide

## Adding New Quotes

Open the relevant JSON file in `/data` and append a new quote object:

```json
{
    "text": "Your inspiring quote here.",
    "author": "Author Name",
    "tags": ["tag1", "tag2"]
}
```

See [quote-format.md](quote-format.md) for full schema details.

## Adding a New Category

1. Create a new file in `/data`, e.g., `leadership.json`.
2. Fill it with an array of quote objects.
3. Open `/src/quote-engine.js` and add the category name to the `CATEGORIES` array:

```js
const CATEGORIES = [
    "general",
    "success",
    "mindfulness",
    "creativity",
    "leadership",
];
```

The UI will automatically generate a new chip button for the category.

## Customizing the Theme

All colors are defined as CSS custom properties in `styles.css`. To change the color scheme:

### Light theme

Edit the `:root` selector:

```css
:root {
    --accent: #34d399; /* Primary accent */
    --bg-primary: #f0faf4; /* Page background */
    --bg-card: #ffffff; /* Quote card background */
    /* ... */
}
```

### Dark theme

Edit the `[data-theme="dark"]` selector similarly.

## Customizing Fonts

Update the `--font-body` and `--font-quote` properties in `:root`:

```css
:root {
    --font-body: "Inter", system-ui, sans-serif;
    --font-quote: "Merriweather", Georgia, serif;
}
```

## Customizing Animations

The quote card transition is controlled by the `.fade-in` / `.fade-out` classes and the `@keyframes fadeIn` rule in `styles.css`. Adjust the duration or easing to your preference.

The customize panel uses `max-height` and `opacity` transitions with timing defined in the `.customize-panel` rule.

## Replacing the Logo

Replace `assets/logo.svg` with your own SVG file. Keep the same filename, or update the `<img>` tag in `index.html` and the `<link rel="icon">` accordingly.
