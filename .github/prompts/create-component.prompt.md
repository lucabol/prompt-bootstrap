# Create New Bootstrap Component

Use this workflow to create a new JavaScript component following Bootstrap's conventions.

## Prerequisites

- Component concept is defined
- SCSS styles are planned
- Accessibility requirements identified

## Workflow Steps

### Step 1: Generate Component JavaScript

Create `js/src/{component-name}.js` extending `BaseComponent`:

```javascript
/**
 * --------------------------------------------------------------------------
 * Bootstrap {component-name}.js
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/main/LICENSE)
 * --------------------------------------------------------------------------
 */

import BaseComponent from './base-component.js'
import EventHandler from './dom/event-handler.js'
import SelectorEngine from './dom/selector-engine.js'
import { defineJQueryPlugin } from './util/index.js'

/**
 * Constants
 */
const NAME = '{componentName}'
const DATA_KEY = `bs.${NAME}`
const EVENT_KEY = `.${DATA_KEY}`
const DATA_API_KEY = '.data-api'

const EVENT_SHOW = `show${EVENT_KEY}`
const EVENT_SHOWN = `shown${EVENT_KEY}`
const EVENT_HIDE = `hide${EVENT_KEY}`
const EVENT_HIDDEN = `hidden${EVENT_KEY}`

const SELECTOR_DATA_TOGGLE = '[data-bs-toggle="{componentName}"]'

const Default = {
  // Define default options
}

const DefaultType = {
  // Define option types for validation
}

/**
 * Class definition
 */
class ComponentName extends BaseComponent {
  constructor(element, config) {
    super(element, config)
    // Initialize component
  }

  // Getters
  static get NAME() {
    return NAME
  }

  static get Default() {
    return Default
  }

  static get DefaultType() {
    return DefaultType
  }

  // Public methods
  show() {
    // Implementation
  }

  hide() {
    // Implementation
  }

  // Static methods
  static jQueryInterface(config) {
    return this.each(function () {
      const data = ComponentName.getOrCreateInstance(this, config)
      if (typeof config === 'string') {
        if (typeof data[config] === 'undefined') {
          throw new TypeError(`No method named "${config}"`)
        }
        data[config]()
      }
    })
  }
}

/**
 * Data API initialization
 */
EventHandler.on(document, `click${EVENT_KEY}${DATA_API_KEY}`, SELECTOR_DATA_TOGGLE, function (event) {
  // Handle data-api click
})

defineJQueryPlugin(ComponentName)

export default ComponentName
```

### Step 2: Add Export to Index Files

Add to `js/index.esm.js`:
```javascript
export { default as ComponentName } from './src/component-name.js'
```

Add to `js/index.umd.js`:
```javascript
import ComponentName from './src/component-name.js'
// Add to export object
```

### Step 3: Create SCSS Styles

Create `scss/_component-name.scss`:

```scss
// scss-docs-start component-name-variables
$component-name-padding-y: $spacer !default;
$component-name-padding-x: $spacer !default;
$component-name-bg: $white !default;
$component-name-border-radius: $border-radius !default;
// scss-docs-end component-name-variables

.component-name {
  padding: $component-name-padding-y $component-name-padding-x;
  background-color: $component-name-bg;
  @include border-radius($component-name-border-radius);
}
```

Import in `scss/bootstrap.scss`:
```scss
@import "component-name";
```

### Step 4: Create Unit Tests

Create `js/tests/unit/component-name.spec.js` (see test-engineer agent).

### Step 5: Create Documentation

Create `site/src/content/docs/components/component-name.mdx`.

### Step 6: Verify Build

```bash
npm run dist          # Build CSS and JS
npm run js-test       # Run tests
npm run docs-serve    # Preview docs
```

## Checklist

- [ ] Component extends `BaseComponent`
- [ ] Static properties defined (NAME, Default, DefaultType)
- [ ] DOM utilities used (not raw DOM APIs)
- [ ] Events properly namespaced
- [ ] jQuery plugin registered
- [ ] Data API implemented
- [ ] SCSS variables use `!default`
- [ ] Unit tests written
- [ ] Documentation created
- [ ] Accessibility verified
