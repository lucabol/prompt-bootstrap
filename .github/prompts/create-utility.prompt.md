# Create Utility Class

Use this workflow to add new utility classes to Bootstrap's utility API.

## Understanding the Utility API

Bootstrap generates utility classes from SCSS maps defined in `scss/_utilities.scss`. The API automatically generates responsive variants, state variants, and handles RTL.

## Workflow Steps

### Step 1: Define the Utility

Add to `scss/_utilities.scss` in the `$utilities` map:

```scss
$utilities: map-merge(
  $utilities,
  (
    "new-utility": (
      property: css-property,          // The CSS property to set
      class: utility-class,            // Class name prefix (optional, uses key if omitted)
      values: (
        1: value1,
        2: value2,
        custom: customValue,
      ),
      responsive: true,                // Generate responsive variants
      rfs: false,                      // Use fluid scaling
      print: false,                    // Generate print variants
    ),
  )
);
```

### Step 2: Common Utility Patterns

#### Simple Values
```scss
"opacity": (
  property: opacity,
  values: (
    0: 0,
    25: .25,
    50: .5,
    75: .75,
    100: 1,
  )
),
```
Generates: `.opacity-0`, `.opacity-25`, etc.

#### With Custom Class Name
```scss
"width": (
  property: width,
  class: w,
  values: (
    25: 25%,
    50: 50%,
    75: 75%,
    100: 100%,
    auto: auto,
  )
),
```
Generates: `.w-25`, `.w-50`, etc.

#### Responsive Variants
```scss
"display": (
  responsive: true,
  property: display,
  class: d,
  values: inline inline-block block grid table flex inline-flex none
),
```
Generates: `.d-none`, `.d-md-block`, `.d-lg-flex`, etc.

#### State Variants
```scss
"background-color": (
  property: background-color,
  class: bg,
  local-vars: (
    "bg-opacity": 1
  ),
  values: map-merge(
    $utilities-bg-colors,
    (
      "transparent": transparent,
    )
  ),
  state: hover,  // Adds hover variants
),
```
Generates: `.bg-primary`, `.bg-primary-hover`, etc.

### Step 3: Add Required Variables

If your utility needs variables, add them to `scss/_variables.scss`:

```scss
// scss-docs-start new-utility-variables
$new-utility-values: (
  1: 0.25rem,
  2: 0.5rem,
  3: 1rem,
) !default;
// scss-docs-end new-utility-variables
```

### Step 4: Build and Test

```bash
npm run css              # Compile CSS
npm run css-lint         # Lint SCSS
```

### Step 5: Document the Utility

Add documentation in `site/src/content/docs/utilities/{utility-name}.mdx`:

```markdown
---
title: "New Utility"
description: "Use new utility classes for..."
group: utilities
---

## Overview

Utility classes for controlling {purpose}.

## Class Reference

| Class | Value |
|-------|-------|
| `.utility-1` | 0.25rem |
| `.utility-2` | 0.5rem |
| `.utility-3` | 1rem |

## Responsive

Add responsive prefixes for breakpoint-specific utilities:

- `.utility-md-1` - Apply at medium breakpoint and up
- `.utility-lg-2` - Apply at large breakpoint and up
```

## Available Utility Options

| Option | Type | Description |
|--------|------|-------------|
| `property` | string/list | CSS property(ies) |
| `values` | map/list | Values to generate |
| `class` | string | Class prefix |
| `css-var` | boolean | Use CSS variable |
| `css-variable-name` | string | Custom CSS var name |
| `local-vars` | map | Local CSS variables |
| `state` | string | State variant (hover, focus) |
| `responsive` | boolean | Generate responsive classes |
| `rfs` | boolean | Use responsive font sizes |
| `print` | boolean | Generate print classes |
| `rtl` | boolean | Enable RTL support |

## Checklist

- [ ] Utility added to `$utilities` map
- [ ] Variables defined with `!default`
- [ ] SCSS compiles without errors
- [ ] Stylelint passes
- [ ] Documentation created
- [ ] Responsive variants work correctly
