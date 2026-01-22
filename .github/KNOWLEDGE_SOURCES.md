# External Knowledge Sources

This document lists recommended external documentation to enhance AI context for Bootstrap development.

## Core Technologies

### Sass/SCSS
- **Official Documentation:** https://sass-lang.com/documentation
- **Sass Guidelines:** https://sass-guidelin.es/
- Topics: Variables, mixins, functions, @use/@forward, maps

### JavaScript ES6+
- **MDN JavaScript Guide:** https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide
- **ES6 Features:** https://es6-features.org/
- Topics: Classes, modules, arrow functions, destructuring, spread operator

### Popper.js
- **Official Documentation:** https://popper.js.org/docs/v2/
- Topics: Positioning, modifiers, virtual elements
- Used by: Dropdown, Tooltip, Popover components

## Build Tools

### Rollup
- **Official Documentation:** https://rollupjs.org/guide/en/
- Topics: Configuration, plugins, output formats (ESM, UMD)

### Karma & Jasmine
- **Karma Documentation:** https://karma-runner.github.io/latest/index.html
- **Jasmine Documentation:** https://jasmine.github.io/
- Topics: Test configuration, async testing, spies, matchers

### Astro
- **Official Documentation:** https://docs.astro.build/
- Topics: Content collections, MDX, components, layouts

## Web Standards

### Accessibility (a11y)
- **WAI-ARIA Authoring Practices:** https://www.w3.org/WAI/ARIA/apg/
- **WCAG Guidelines:** https://www.w3.org/WAI/WCAG21/quickref/
- Topics: Keyboard navigation, ARIA roles/states, focus management

### CSS
- **MDN CSS Reference:** https://developer.mozilla.org/en-US/docs/Web/CSS/Reference
- **CSS Logical Properties:** https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties
- Topics: Custom properties, logical properties, transitions

### RTL Support
- **RTL Styling Guide:** https://rtlstyling.com/
- Topics: Logical properties, bidirectional text, mirroring

## Bootstrap-Specific

### Official Resources
- **Bootstrap Documentation:** https://getbootstrap.com/docs/5.3/
- **Bootstrap Blog:** https://blog.getbootstrap.com/
- **Bootstrap Icons:** https://icons.getbootstrap.com/

### Community Resources
- **Bootstrap GitHub Discussions:** https://github.com/twbs/bootstrap/discussions
- **Stack Overflow [bootstrap-5]:** https://stackoverflow.com/questions/tagged/bootstrap-5

## Code Quality

### Code Guide
- **mdo/code-guide:** https://github.com/mdo/code-guide
- Topics: HTML/CSS coding standards used by Bootstrap

### ESLint XO
- **XO Configuration:** https://github.com/xojs/xo
- Topics: JavaScript style rules enforced in Bootstrap

### Stylelint
- **Stylelint Documentation:** https://stylelint.io/
- Topics: CSS/SCSS linting rules

## Recommended for AI Context Enhancement

Consider adding these resources via MCP or context ingestion:

1. **Bootstrap source files** - Already available in workspace
2. **WAI-ARIA patterns** - For accessibility implementation
3. **Popper.js API** - For positioning-related components
4. **Sass built-in modules** - For advanced SCSS features

## Integration Notes

When integrating external documentation:

1. **Prioritize official sources** over third-party tutorials
2. **Version-match** documentation to tool versions in package.json
3. **Focus on API references** rather than getting-started guides
4. **Include changelog/migration** docs for major version updates
