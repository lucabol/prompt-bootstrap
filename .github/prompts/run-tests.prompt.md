# Run Full Test Suite

Use this workflow to run comprehensive tests and quality checks before submitting a PR.

## Quick Commands

### Run Everything
```bash
npm run test
```
This runs: `lint` → `dist` → `js-test` → `docs-build` → `docs-lint`

### Individual Checks

| Check | Command | Purpose |
|-------|---------|---------|
| Lint All | `npm run lint` | ESLint + Stylelint + lockfile-lint |
| JS Lint | `npm run js-lint` | JavaScript linting only |
| CSS Lint | `npm run css-lint` | SCSS/CSS linting only |
| JS Tests | `npm run js-test` | Karma unit tests |
| CSS Tests | `npm run css-test` | SCSS unit tests |
| Docs Build | `npm run docs-build` | Build documentation |
| Docs Lint | `npm run docs-lint` | Prettier + HTML validation |

## Pre-PR Checklist Workflow

### Step 1: Lint Your Code
```bash
npm run lint
```

Fix any errors. Common issues:
- ESLint: Missing semicolons, unused variables
- Stylelint: Invalid SCSS syntax, wrong variable naming

### Step 2: Build Distribution
```bash
npm run dist
```

This compiles CSS and JS. Ensure no build errors.

### Step 3: Run JavaScript Tests
```bash
npm run js-test
```

For debugging failing tests:
```bash
npm run js-debug
```

### Step 4: Run SCSS Tests
```bash
npm run css-test
```

### Step 5: Build and Lint Documentation
```bash
npm run docs
```

### Step 6: Visual Verification
```bash
npm run docs-serve
```
Open http://localhost:9001 and verify changes visually.

## Fixing Common Issues

### ESLint Errors
```bash
# See all errors
npm run js-lint

# Common fixes are auto-fixable
npx eslint --fix "path/to/file.js"
```

### Stylelint Errors
```bash
# See all errors
npm run css-lint

# Check specific file
npx stylelint "scss/_component.scss"
```

### Prettier Formatting (Docs)
```bash
# Check formatting
npm run docs-prettier-check

# Auto-fix
npm run docs-prettier-format
```

## BrowserStack Testing

For cross-browser testing (maintainers only):
```bash
npm run js-test-cloud
```

Requires `BROWSERSTACK_USERNAME` and `BROWSERSTACK_ACCESS_KEY` environment variables.

## Bundle Size Check

```bash
npm run bundlewatch
```

Checks that built files don't exceed size limits.
