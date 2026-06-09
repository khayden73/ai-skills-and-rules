# HTML Rules

- **Semantic HTML**: Use semantic HTML where appropriate.
- **Validation**: Follow HTML validation rules.
- **Accessibility**: Adhere to accessibility best practices.
- **Headings**: Maintain proper heading hierarchy (`h1` → `h2` → `h3`). Never skip levels. One `h1` per page.
- **Buttons vs links**: Use `<button>` for actions, `<a>` for navigation. Never use `<div>` or `<span>` as clickable elements.
- **Icon-only buttons**: Always include `aria-label` on buttons that have no visible text.
- **Images**: Always provide meaningful `alt` text. Use `alt=""` only for purely decorative images.
- **Forms**: Every input must have an associated `<label>`.
- **Keyboard Navigation**: Tab order must be the order in which elements appear in the DOM.


## Examples
```html
// ✅ GOOD – use section to separate children of a div
<div>
    <section>section 1</section>
    <section>section 2</section>
</div>
```

```html
<div>
    <article>
        main article content goes here
    </article>
    <aside>for content sidebar</aside>
</div>
```

```html
// ✅ GOOD – button for action, aria-label for icon-only
<button aria-label="Toggle theme"><SunIcon /></button>

// ✅ GOOD – anchor for navigation
<a href="/blog">Read blog</a>

// ❌ BAD – div as button, no accessibility
<div onclick="toggle()"><SunIcon /></div>
```