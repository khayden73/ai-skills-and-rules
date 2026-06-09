# CSS Rules

- **Mobile-first breakpoints**: Use `min-width` media queries. Base styles are mobile, then layer on tablet (481px) and desktop (769px).
- **CSS custom properties for breakpoint values**: When a value changes between breakpoints, define it as a custom property on the component root and override it inside `@media` blocks. Don't redeclare full rule blocks.
- **Units**: Use `rem` and `em` instead of `px`. Exceptions: `1px` borders and media query values.
- **CSS nesting**: Use native CSS nesting (`&`) for hover/focus states, pseudo-elements, and media queries inside their parent selectors.
- **CSS Modules**: Each component with visual styling gets its own `.module.css` file. Global layout styles go in `globals.css`.
- **Class naming**: Use descriptive, component-scoped names (e.g. `.siteFooter`, `.footerText`). Avoid generic names like `.footer`, `.text`, `.toggle`.
- **Color variables**: All colors come from CSS custom properties defined in global files such as `tokens.css` or  `pallet.css`.
- **Never** use hardcoded color values in component styles.
- **WCAG contrast**: follow WCAG guidelines for color contrast between font colors and the background
- **Font sizes**: NO font sizes should be smaller than 16px
- **Keep it DRY**: Don't Repeat Yourself. If styles exist in global, they should not be replicated in component styles. Stick to best practices of "the cascade".
- **Global Fonts**: font sizes, family, colors and spacing defined globally. If there is a need to set any font styles at the component level, ask first, otherwise defer to global
