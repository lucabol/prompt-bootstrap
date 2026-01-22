# Bootstrap Global Copilot Instructions

> This file defines the global AI coding standards for the Bootstrap repository (v5.3.8).

## Project Identity

- **Project:** Bootstrap - The most popular front-end framework
- **Version:** 5.3.8 (Semantic Versioning)
- **License:** MIT
- **Primary Languages:** JavaScript (ES2015+), SCSS/Sass, HTML

## Tech Stack (Exact Versions)

| Technology | Version | Purpose |
|------------|---------|---------|
| Node.js | LTS | Runtime environment |
| Sass | 1.78.0 | CSS preprocessor |
| Rollup | 4.54.0 | JavaScript bundler |
| Babel | 7.28.5 | JavaScript transpilation |
| Terser | 5.44.1 | JavaScript minification |
| PostCSS | 8.5.6 | CSS processing |
| Autoprefixer | 10.4.23 | Vendor prefixing |
| Karma | 6.4.4 | JavaScript test runner |
| Jasmine | 5.13.0 | Testing framework |
| Astro | 5.16.6 | Documentation site builder |
| ESLint | 8.57.1 | JavaScript linting |
| Stylelint | 16.26.1 | CSS/SCSS linting |
| @popperjs/core | 2.11.8 | Positioning engine (peer dependency) |

## Golden Rules

### 1. Component Architecture
- All JavaScript components **MUST** extend `BaseComponent` from `js/src/base-component.js`
- Components use the static `NAME` property for data-attribute registration (`bs.{NAME}`)
- Always use the internal `Data`, `EventHandler`, `SelectorEngine`, and `Manipulator` DOM utilities
- Never manipulate DOM directly without using Bootstrap's abstraction layer

### 2. JavaScript Patterns
- Use ES6+ class syntax with static getters for `NAME`, `DATA_KEY`, `EVENT_KEY`, `DefaultType`, and `Default`
- All events must use namespaced event names (`.bs.{componentName}`)
- Support both programmatic API and data-attribute initialization
- Maintain jQuery compatibility via `defineJQueryPlugin()` utility
- Components must be tree-shakeable (individual ESM exports)

### 3. SCSS/CSS Standards
- Follow the variable naming convention: `$component-state-property-size`
- All variables must use `!default` flag for customization
- Use Bootstrap's mixin library from `scss/mixins/`
- Support RTL via logical properties and the RTL build pipeline
- Maintain CSS custom properties (CSS variables) for runtime theming

### 4. Accessibility Requirements
- All interactive components must be keyboard navigable
- Use appropriate ARIA attributes (`aria-expanded`, `aria-controls`, `aria-hidden`)
- Ensure proper focus management for modals, dropdowns, and overlays
- Test with screen readers and keyboard-only navigation

### 5. Documentation
- All components must have corresponding documentation in `site/src/content/docs/`
- Use Astro MDX format for documentation pages
- Include live examples with proper code snippets

## Local Automation Commands

| Task | Command | Description |
|------|---------|-------------|
| Full Build | `npm run dist` | Compile CSS and JS |
| CSS Only | `npm run css` | Compile, prefix, RTL, minify CSS |
| JS Only | `npm run js` | Compile and minify JavaScript |
| Lint All | `npm run lint` | Run ESLint, Stylelint, lockfile-lint |
| Test All | `npm run test` | Lint + build + test + docs |
| JS Tests | `npm run js-test` | Run Karma unit tests |
| CSS Tests | `npm run css-test` | Run SCSS unit tests |
| Watch Mode | `npm run watch` | Watch CSS/JS for changes |
| Dev Server | `npm run docs-serve` | Start Astro dev server on port 9001 |
| Start | `npm run start` | Watch + docs-serve in parallel |

## File Organization

```
bootstrap/
├── js/
│   ├── src/              # ES6+ component source
│   │   ├── dom/          # DOM abstraction utilities
│   │   └── util/         # Helper utilities
│   └── tests/            # Karma/Jasmine tests
├── scss/
│   ├── _*.scss           # Partial stylesheets
│   ├── mixins/           # Reusable SCSS mixins
│   ├── utilities/        # Utility classes generator
│   └── forms/            # Form-specific styles
├── build/                # Build scripts (Rollup, PostCSS)
├── dist/                 # Compiled output (git-ignored)
└── site/                 # Astro documentation site
```

## Code Style Enforcement

- **JavaScript:** ESLint with XO config (enforced via `npm run js-lint`)
- **SCSS/CSS:** Stylelint with Bootstrap-specific rules (enforced via `npm run css-lint`)
- **Formatting:** Prettier for documentation files
- **Editor:** Use `.editorconfig` settings

## Commit & PR Guidelines

- Follow conventional commit messages
- PRs with JavaScript changes must include unit tests
- All HTML/CSS must conform to the [Code Guide](https://github.com/mdo/code-guide)
- Run `npm run test` before submitting PRs
