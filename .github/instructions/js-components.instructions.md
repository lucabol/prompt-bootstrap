---
applyTo: "js/src/*.js"
---

# JavaScript Component Development Rules

## File Structure Pattern

Every Bootstrap component in `js/src/` must follow this structure:

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
// ... other imports

/**
 * Constants
 */
const NAME = 'componentName'
const DATA_KEY = `bs.${NAME}`
const EVENT_KEY = `.${DATA_KEY}`
const DATA_API_KEY = '.data-api'

const EVENT_SHOW = `show${EVENT_KEY}`
const EVENT_SHOWN = `shown${EVENT_KEY}`
const EVENT_HIDE = `hide${EVENT_KEY}`
const EVENT_HIDDEN = `hidden${EVENT_KEY}`

const Default = {
  // default options
}

const DefaultType = {
  // type validation
}

/**
 * Class definition
 */
class ComponentName extends BaseComponent {
  // implementation
}

export default ComponentName
```

## Required Static Properties

All components must define these static getters:

- `static get NAME()` - Component name (lowercase)
- `static get Default()` - Default configuration object
- `static get DefaultType()` - Type validation object

## DOM Utilities (MUST USE)

| Utility | Import | Purpose |
|---------|--------|---------|
| `Data` | `./dom/data.js` | Component instance storage |
| `EventHandler` | `./dom/event-handler.js` | Event binding/unbinding |
| `SelectorEngine` | `./dom/selector-engine.js` | DOM queries |
| `Manipulator` | `./dom/manipulator.js` | Data attribute manipulation |

## Event Naming Convention

```javascript
// Pattern: {eventName}{EVENT_KEY}
const EVENT_SHOW = `show${EVENT_KEY}`      // show.bs.modal
const EVENT_SHOWN = `shown${EVENT_KEY}`    // shown.bs.modal
const EVENT_CLICK = `click${EVENT_KEY}`    // click.bs.modal
const EVENT_CLICK_DATA_API = `click${EVENT_KEY}${DATA_API_KEY}` // click.bs.modal.data-api
```

## Utility Functions

Import from `./util/index.js`:

- `getElement()` - Resolve element from selector/jQuery/node
- `isElement()` - Check if object is DOM element
- `isVisible()` - Check element visibility
- `isDisabled()` - Check if element is disabled
- `reflow()` - Trigger reflow for animations
- `executeAfterTransition()` - Wait for CSS transitions
- `defineJQueryPlugin()` - Register jQuery plugin

## Testing Requirements

- All new components need tests in `js/tests/unit/`
- Use Jasmine syntax with Karma runner
- Test both programmatic API and data-attribute initialization
- Mock DOM as needed using test helpers from `js/tests/helpers/`
