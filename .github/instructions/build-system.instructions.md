---
applyTo: "build/**/*"
---

# Build System Rules

## Build Tools Overview

| Tool | File | Purpose |
|------|------|---------|
| Rollup | `rollup.config.mjs` | JavaScript bundling (ESM/UMD) |
| PostCSS | `postcss.config.mjs` | CSS processing, RTL, autoprefixer |
| Terser | via npm scripts | JavaScript minification |
| CleanCSS | via npm scripts | CSS minification |
| Sass | via npm scripts | SCSS compilation |

## Rollup Configuration

The bundler produces three outputs:

1. **Standalone** (`bootstrap.js`) - UMD format, Popper external
2. **Standalone ESM** (`bootstrap.esm.js`) - ESM format, Popper external
3. **Bundle** (`bootstrap.bundle.js`) - UMD format, Popper included

Environment variables control output:
```bash
BUNDLE=true   # Include Popper
ESM=true      # Output ESM format
```

## Build Scripts

### Full Build Pipeline
```bash
npm run dist          # CSS + JS
npm run css           # css-compile → css-prefix → css-rtl → css-minify
npm run js            # js-compile → js-minify
```

### Individual Steps
```bash
# CSS
npm run css-compile        # Sass → CSS
npm run css-prefix         # Add vendor prefixes
npm run css-rtl            # Generate RTL versions
npm run css-minify         # Minify CSS

# JavaScript
npm run js-compile-standalone      # Single file, Popper external
npm run js-compile-bundle          # With Popper bundled
npm run js-compile-plugins         # Individual plugins
npm run js-minify                  # Minify all JS
```

## Custom Build Scripts

| Script | Description |
|--------|-------------|
| `banner.mjs` | Generate file header comments |
| `build-plugins.mjs` | Build individual plugin files |
| `change-version.mjs` | Version bump utility |
| `generate-sri.mjs` | Generate SRI hashes for CDN |
| `zip-examples.mjs` | Package examples for release |
| `vnu-jar.mjs` | HTML validation |

## Adding New Build Steps

1. Create script in `build/` directory
2. Export function or use as CLI
3. Add npm script to `package.json`
4. Document in this file

## Watch Mode

```bash
npm run watch           # Watch all
npm run watch-css-main  # SCSS changes
npm run watch-js-main   # JS changes
```

Uses `nodemon` for file watching with automatic rebuild.
