---
applyTo: "scss/**/*.scss"
---

# SCSS/Sass Development Rules

## Variable Naming Convention

Follow the `$component-state-property-size` formula:

```scss
// ✅ Correct
$modal-header-padding-y: 1rem !default;
$btn-disabled-opacity: .65 !default;
$nav-link-hover-color: null !default;

// ❌ Incorrect
$modalHeaderPadding: 1rem;      // No camelCase
$btn-opacity-disabled: .65;     // Wrong order
$navLinkColor: blue;            // Missing !default
```

## Required `!default` Flag

ALL variables must use `!default` to allow user customization:

```scss
$primary: #0d6efd !default;
$spacer: 1rem !default;
$border-radius: 0.375rem !default;
```

## File Organization

| Pattern | Purpose |
|---------|---------|
| `_variables.scss` | All Sass variables with `!default` |
| `_variables-dark.scss` | Dark mode variable overrides |
| `_mixins.scss` | Mixin imports aggregator |
| `scss/mixins/*.scss` | Individual mixin definitions |
| `scss/forms/*.scss` | Form-specific styles |
| `scss/helpers/*.scss` | Utility helper classes |
| `scss/utilities/_api.scss` | Utility API generator |

## Mixin Usage

Import and use Bootstrap's mixin library:

```scss
// Required imports at top
@import "mixins/breakpoints";
@import "mixins/border-radius";
@import "mixins/box-shadow";

// Responsive breakpoints
@include media-breakpoint-up(md) {
  // Styles for md and larger
}

@include media-breakpoint-down(lg) {
  // Styles for lg and smaller
}

// Border radius
@include border-radius($border-radius);
@include border-top-radius($border-radius-lg);

// Box shadows
@include box-shadow($box-shadow);
```

## CSS Custom Properties (Variables)

Use CSS custom properties for runtime theming:

```scss
// Define in :root or component
:root {
  --#{$prefix}primary: #{$primary};
  --#{$prefix}body-bg: #{$body-bg};
}

// Use in styles
.component {
  color: var(--#{$prefix}body-color);
  background-color: var(--#{$prefix}body-bg);
}
```

## RTL Support

Use logical properties for RTL compatibility:

```scss
// ✅ Use logical properties
margin-inline-start: 1rem;
padding-inline-end: 0.5rem;
border-start-start-radius: 0.25rem;

// ❌ Avoid physical properties for RTL-sensitive styles
margin-left: 1rem;   // Use margin-inline-start
padding-right: 0.5rem; // Use padding-inline-end
```

## Documentation Comments

Use `// scss-docs-start` and `// scss-docs-end` markers:

```scss
// scss-docs-start theme-color-variables
$primary:   $blue !default;
$secondary: $gray-600 !default;
$success:   $green !default;
// scss-docs-end theme-color-variables
```

## Testing SCSS

Run SCSS unit tests with:
```bash
npm run css-test
```

Tests use `sass-true` and are located in `scss/tests/`.
