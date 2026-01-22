---
applyTo: "js/tests/**/*"
---

# JavaScript Testing Rules

## Testing Stack

- **Runner:** Karma 6.4.4
- **Framework:** Jasmine 5.13.0
- **Browsers:** Chrome, Firefox (via karma-detect-browsers)
- **Coverage:** Istanbul

## Test File Structure

```
js/tests/
├── karma.conf.js         # Karma configuration
├── helpers/              # Test utilities and fixtures
├── unit/                 # Unit tests for each component
├── integration/          # Integration tests
└── visual/               # Visual regression tests
```

## Unit Test Pattern

```javascript
import ComponentName from '../../src/component-name.js'
import { clearFixture, getFixture, createEvent } from '../helpers/fixture.js'

describe('ComponentName', () => {
  let fixtureEl

  beforeAll(() => {
    fixtureEl = getFixture()
  })

  afterEach(() => {
    clearFixture()
  })

  describe('VERSION', () => {
    it('should return plugin version', () => {
      expect(ComponentName.VERSION).toEqual(jasmine.any(String))
    })
  })

  describe('constructor', () => {
    it('should create instance', () => {
      fixtureEl.innerHTML = '<div class="component"></div>'
      const element = fixtureEl.querySelector('.component')
      const instance = new ComponentName(element)

      expect(instance).toBeInstanceOf(ComponentName)
      expect(ComponentName.getInstance(element)).toBe(instance)
    })
  })

  describe('method', () => {
    it('should do expected behavior', () => {
      // Test implementation
    })
  })
})
```

## Test Helpers

Located in `js/tests/helpers/`:

| Helper | Purpose |
|--------|---------|
| `fixture.js` | DOM fixture management |
| `event.js` | Event simulation |
| `pointer-event.js` | Pointer event mocking |

## Running Tests

```bash
npm run js-test           # Run all JS tests
npm run js-test-karma     # Karma tests only
npm run js-test-jquery    # Test with jQuery
npm run js-debug          # Debug mode
npm run js-test-cloud     # BrowserStack tests
```

## What to Test

1. **Static properties** - VERSION, NAME, Default, DefaultType
2. **Constructor** - Instance creation, options parsing
3. **Public methods** - show(), hide(), toggle(), dispose()
4. **Events** - Custom events fire correctly
5. **Data API** - Data attribute initialization
6. **Edge cases** - Missing elements, invalid options

## Coverage Requirements

- All public methods must have tests
- Event handlers must be tested
- Data attribute initialization must be tested
- Dispose/cleanup must be verified
