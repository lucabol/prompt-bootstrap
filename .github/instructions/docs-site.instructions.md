---
applyTo: "site/**/*"
---

# Documentation Site Rules (Astro)

## Technology Stack

- **Framework:** Astro 5.16.6
- **Content Format:** MDX (Markdown + JSX)
- **Search:** Algolia DocSearch
- **Styling:** Bootstrap's own CSS

## File Structure

```
site/
├── astro.config.ts       # Astro configuration
├── src/
│   ├── content/docs/     # Documentation MDX files
│   ├── layouts/          # Page layouts
│   ├── components/       # Astro components
│   ├── scss/             # Site-specific styles
│   └── assets/           # Static assets
├── static/               # Unprocessed static files
└── data/                 # YAML/JSON data files
```

## Documentation Page Format

```mdx
---
title: "Component Name"
description: "Brief description for SEO"
group: "components"
toc: true
---

import CallOut from '@components/CallOut.astro'

# Component Name

Brief introduction paragraph.

## Overview

<CallOut type="info">
  Important information callout
</CallOut>

## Examples

{/* Live code example */}
```html
<div class="component">Example markup</div>
```

## Sass Variables

Available customization variables...

## JavaScript Behavior

API documentation...
```

## Local Commands

| Task | Command |
|------|---------|
| Dev Server | `npm run docs-serve` |
| Build Docs | `npm run docs-build` |
| Lint Docs | `npm run docs-lint` |
| Format | `npm run docs-prettier-format` |
| Check Links | `npm run docs-vnu` |

## Code Examples

### Syntax Highlighting

Use fenced code blocks with language identifier:

````markdown
```html
<button class="btn btn-primary">Button</button>
```

```scss
.custom-class {
  color: $primary;
}
```

```js
const modal = new bootstrap.Modal('#myModal')
```
````

### Live Examples

For interactive examples, include proper HTML structure that can be rendered.

## Frontmatter Requirements

| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Page title |
| `description` | Yes | SEO description |
| `group` | No | Navigation group |
| `toc` | No | Show table of contents |

## Assets and Linking

- Use relative paths for internal links
- Reference Bootstrap CSS/JS from built `dist/` folder
- Images in `site/static/` are copied as-is
