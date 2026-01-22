# Add Component Option

Use this workflow to add a new configuration option to an existing Bootstrap component.

## Workflow Steps

### Step 1: Identify the Component

Locate the component source file in `js/src/{component}.js`.

### Step 2: Add Default Value

Add the new option to the `Default` object:

```javascript
const Default = {
  // ... existing options
  newOption: false  // Add your option with sensible default
}
```

### Step 3: Add Type Validation

Add type validation to `DefaultType`:

```javascript
const DefaultType = {
  // ... existing types
  newOption: 'boolean'  // 'boolean' | 'string' | 'number' | 'object' | 'element'
}
```

### Step 4: Implement the Option

Use the option in your component logic:

```javascript
// Access via this._config
if (this._config.newOption) {
  // Option-specific behavior
}
```

### Step 5: Support Data Attributes

Options automatically support `data-bs-{option-name}` attributes via `Manipulator`.

For kebab-case conversion, ensure the data attribute matches:
- JS: `newOption`
- HTML: `data-bs-new-option`

### Step 6: Update SCSS (if visual)

If the option affects styling, add corresponding SCSS variables:

```scss
// In scss/_component.scss or scss/_variables.scss
$component-new-option-value: 1rem !default;
```

### Step 7: Add Tests

Create tests in `js/tests/unit/{component}.spec.js`:

```javascript
describe('newOption', () => {
  it('should have default value', () => {
    const instance = new Component(element)
    expect(instance._config.newOption).toBe(false)
  })

  it('should respect custom value', () => {
    const instance = new Component(element, { newOption: true })
    expect(instance._config.newOption).toBe(true)
  })

  it('should support data attribute', () => {
    element.setAttribute('data-bs-new-option', 'true')
    const instance = new Component(element)
    expect(instance._config.newOption).toBe(true)
  })
})
```

### Step 8: Update Documentation

Add documentation in `site/src/content/docs/components/{component}.mdx`:

```markdown
### Options

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `newOption` | boolean | `false` | Description of what this option does |
```

Add usage example:

```html
<!-- Via data attribute -->
<div data-bs-toggle="component" data-bs-new-option="true">...</div>
```

```javascript
// Via JavaScript
const instance = new bootstrap.Component(element, {
  newOption: true
})
```

## Verification

```bash
npm run js-lint           # Check JS syntax
npm run js-test           # Run tests
npm run docs-serve        # Verify documentation
```

## Checklist

- [ ] Option added to `Default` with sensible default value
- [ ] Type validation added to `DefaultType`
- [ ] Option behavior implemented
- [ ] Data attribute support tested
- [ ] Unit tests cover default, custom, and data-attr values
- [ ] Documentation updated with option table
- [ ] Usage examples provided
