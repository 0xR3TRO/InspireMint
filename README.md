<div align="center">

# 🌿 InspireMint

**A personalized motivational quote generator built with pure HTML, CSS & JavaScript.**

[Live Demo](#) · [Documentation](docs/overview.md) · [Report Bug](https://github.com/0xR3TRO/InspireMint/issues)

</div>

---

## About

InspireMint is a modern, lightweight web application that delivers motivational quotes with a beautiful, minimal UI. Users can personalize their experience by selecting categories, filtering by tags, searching with keywords, and switching between light and dark themes — all without any frameworks or build tools.

## Features

- **Random Quote Generation** — Get a fresh motivational quote with one click
- **Category Selection** — Choose from General, Success, Mindfulness, and Creativity
- **Tag Filtering** — Narrow quotes by themes like _discipline_, _courage_, _growth_
- **Keyword Search** — Free-text search across quotes, authors, and tags
- **Dark / Light Mode** — Toggle theme with preference saved in `localStorage`
- **Mobile-First Responsive Design** — Scales from phones to wide screens
- **Smooth Animations** — Fade-in/fade-out transitions on quote change
- **No Dependencies** — Zero frameworks, zero build step, pure web standards

## Repository Structure

```
InspireMint/
├── index.html              Main HTML page
├── styles.css              All styles (light & dark themes)
├── script.js               Entry point (ES Module)
├── src/
│   ├── quote-engine.js     Quote loading & random selection
│   ├── quote-filter.js     Category, tag & keyword filtering
│   ├── ui-controller.js    DOM rendering, events, animations
│   ├── theme.js            Light/dark toggle + localStorage
│   └── utils.js            Helpers (random, debounce, etc.)
├── data/
│   ├── general.json        General motivational quotes
│   ├── success.json        Success-themed quotes
│   ├── mindfulness.json    Mindfulness & calm quotes
│   └── creativity.json     Creativity & innovation quotes
├── assets/
│   ├── logo.svg            InspireMint logo
│   └── icons/              Icon assets
├── docs/
│   ├── overview.md         Project overview
│   ├── quote-format.md     Quote JSON schema
│   ├── architecture.md     Module & data flow docs
│   ├── customization.md    How to customize themes & quotes
│   └── integration.md      Embedding InspireMint as a widget
└── README.md               This file
```

## Getting Started

1. **Clone the repository**

    ```bash
    git clone https://github.com/0xR3TRO/InspireMint.git
    cd InspireMint
    ```

2. **Serve locally** (required for ES module `fetch` calls)

    ```bash
    npx serve .
    # or
    python3 -m http.server
    ```

3. **Open in browser**

    Navigate to `http://localhost:3000` (or the port shown) and enjoy!

> **Note:** Opening `index.html` directly via `file://` may not work in all browsers due to CORS restrictions on `fetch()`. Use a local HTTP server instead.

## Quote Format

Each quote is a JSON object with the following structure:

```json
{
    "text": "Believe you can and you're halfway there.",
    "author": "Theodore Roosevelt",
    "tags": ["confidence", "motivation", "success"]
}
```

| Field    | Type       | Description                          |
| -------- | ---------- | ------------------------------------ |
| `text`   | `string`   | The quote text                       |
| `author` | `string`   | Attribution (use `"Unknown"` if N/A) |
| `tags`   | `string[]` | Lowercase theme tags                 |

See [docs/quote-format.md](docs/quote-format.md) for full details.

## Customization

### Adding quotes

Append a new object to any JSON file in `/data`.

### Adding a new category

1. Create a new `.json` file in `/data` (e.g., `leadership.json`).
2. Add the category name to the `CATEGORIES` array in `src/quote-engine.js`.

### Changing colors

Edit the CSS custom properties in `styles.css` under `:root` (light) or `[data-theme="dark"]`.

### Changing fonts

Update `--font-body` and `--font-quote` in `:root`.

See [docs/customization.md](docs/customization.md) for a full guide.

## Future Improvements

- [ ] Fetch quotes from an external API
- [ ] Share quote as image on social media
- [ ] Daily quote widget / notification
- [ ] Favorite quotes with `localStorage` persistence
- [ ] Quote history view
- [ ] Multi-language support
- [ ] Copy quote to clipboard button
- [ ] Keyboard shortcuts for power users

## License

This project is open source and available under the [MIT License](LICENSE).
[Polish](Documents/READMEPL.md)
