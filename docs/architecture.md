# Architecture

## High-Level Data Flow

```
index.html
  └─ script.js  (entry point)
       └─ ui-controller.js
            ├─ quote-engine.js  ← loads JSON from /data
            │     └─ quote-filter.js
            ├─ theme.js
            └─ utils.js
```

1. **`script.js`** — Entry point. Imports and calls `initApp()` on `DOMContentLoaded`.
2. **`ui-controller.js`** — Owns all DOM interactions: rendering quotes, building the customize panel, binding event listeners, and managing animations.
3. **`quote-engine.js`** — Fetches quote data from `/data/*.json`, maintains the in-memory quote pool, and selects random quotes based on active filters.
4. **`quote-filter.js`** — Pure filtering logic. Filters the quote pool by category, tags, and keywords. No side effects.
5. **`theme.js`** — Manages the light/dark theme toggle and persists the user's choice in `localStorage`.
6. **`utils.js`** — Shared helper functions: `getRandomItem`, `shuffleArray`, `normalizeText`, `debounce`.

## Module Responsibilities

### quote-engine.js

- `loadQuotes()` — Fetches all category JSON files in parallel and stores them with a `_category` metadata field.
- `getRandomQuote(filters)` — Applies filters, picks a random quote (avoiding consecutive repeats), and falls back to the general pool if results are empty.
- `getAllTags()` — Returns a sorted, deduplicated list of all tags across every quote.

### quote-filter.js

- `filterByCategory(quotes, category)` — Returns quotes matching the given category.
- `filterByTags(quotes, tags)` — Returns quotes that contain at least one of the specified tags.
- `filterByKeywords(quotes, keywords)` — Free-text search across text, author, and tags.
- `applyFilters(quotes, filterObj)` — Composes the three filters sequentially.

### ui-controller.js

- `initApp()` — Bootstraps the entire application: initializes theme, loads quotes, builds UI, binds events.
- `renderQuote(quote)` — Handles fade-out → content swap → fade-in transition.
- `buildCustomizePanel()` — Dynamically generates category and tag chips from loaded data.

### theme.js

- `initTheme()` — Reads saved preference or falls back to `prefers-color-scheme`.
- `toggleTheme()` — Swaps `data-theme` attribute on `<html>` and persists.

## Data Storage

All quote data lives in static JSON files under `/data`. No build step or server is required — the app uses `fetch()` to load them at runtime.
