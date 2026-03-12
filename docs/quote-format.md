# Quote Format

All quotes are stored as JSON arrays inside the `/data` directory. Each file represents a category.

## Schema

Each quote object follows this structure:

```json
{
    "text": "Believe you can and you're halfway there.",
    "author": "Theodore Roosevelt",
    "tags": ["confidence", "motivation", "success"]
}
```

### Fields

| Field    | Type       | Required | Description                                             |
| -------- | ---------- | -------- | ------------------------------------------------------- |
| `text`   | `string`   | Yes      | The quote text                                          |
| `author` | `string`   | Yes      | Author name. Use `"Unknown"` if not attributed          |
| `tags`   | `string[]` | Yes      | One or more lowercase tags describing the quote's theme |

## File Naming

- One JSON file per category, placed in `/data`.
- File name = category slug (e.g., `success.json`, `creativity.json`).
- The category name is derived from the filename automatically by the quote engine.

## Adding a Quote

1. Open the appropriate category file in `/data`.
2. Append a new object to the array:

```json
{
    "text": "Your new quote here.",
    "author": "Author Name",
    "tags": ["tag1", "tag2"]
}
```

3. Save the file. The quote will appear immediately on next page load.

## Adding a New Category

1. Create a new `.json` file in `/data` (e.g., `leadership.json`).
2. Format it as an array of quote objects following the schema above.
3. Register the category name in `/src/quote-engine.js` by adding it to the `CATEGORIES` array.
