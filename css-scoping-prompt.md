# CSS Scoping Prompt for Microfrontend

Refactor the CSS and HTML in this Webpack/SCSS project to scope styles for microfrontend usage.

## Tasks:
- Add a wrapper class `radar-component` to the root container in the mount function (already done in src/radar.js).
- Prefix all top-level SCSS selectors with `.radar-component` (e.g., change `.hero-banner` to `.radar-component .hero-banner`).
- Do not modify nested selectors (e.g., `&__wrapper` remains as is, since SCSS expands it correctly).
- Update any HTML class attributes in templates and JavaScript-generated elements if they conflict, but keep core functionality intact.
- Ensure D3 selections and event handlers still work.
- Do not change JavaScript logic or data processing.

## Files to Modify:
- src/stylesheets/*.scss: Prefix top-level selectors.
- src/**/*.html: Check for any global classes (unlikely).
- src/**/*.js: Only HTML generation parts if needed.

## Output:
- A summary of changes made, including files modified and examples.
- Ensure the build still works and styles are scoped.

## Notes:
- Top-level selectors are those starting with `.` at the beginning of a line (use regex `^\.`).
- Avoid over-scoping; only add `.radar-component` where it prevents host conflicts.
- Test that the radar renders correctly with scoped styles.
