**Prompt for AI Assistant in `build-your-own-radar` Repo:**

You are working on the `build-your-own-radar` repository, a vanilla JS/D3 app for rendering technology radars. The app is being adapted for microfrontend use, where it will be mounted into another page's DOM. Currently, the app's CSS affects the host page globally, causing style conflicts. To fix this, we need to scope all CSS rules to a specific class (`.radar-app`) so styles only apply inside the radar container.

### Objective
Make the radar app self-contained by scoping its CSS and HTML structure. This ensures it renders correctly in a microfrontend without affecting or requiring overrides from the host page.

### Requirements
- Scope all CSS rules to `.radar-app` (prefix each rule with `.radar-app `).
- Wrap the radar's HTML content in a `<div class="radar-app">` container.
- Update the mount function to use the scoped container.
- Avoid global CSS rules (e.g., `body`, `html`, `*`) that could leak to the host.
- Ensure the app still works standalone (e.g., on its own page).

### Steps to Implement
1. **Review Current Structure**:
   - Examine `src/index.html` (or the main HTML template) for the radar structure.
   - Check `src/radar-plot.css` (or main CSS file) for global rules.

2. **Update HTML Template**:
   - Wrap the main radar content in `<div class="radar-app">...</div>`.
   - Ensure all radar elements (SVG, lists, etc.) are inside this div.

3. **Scope the CSS**:
   - Open the main CSS file (e.g., `radar-plot.css`).
   - Prefix every CSS rule with `.radar-app ` (e.g., change `.radar-plot { ... }` to `.radar-app .radar-plot { ... }`).
   - For global rules like `body { font-family: ... }`, change to `.radar-app { font-family: ... }` or remove if not needed.
   - Use a tool or script for bulk replacement (e.g., sed: `sed -i 's/^/.radar-app /g' radar-plot.css`, but manually verify).

4. **Update the Mount Function** (`src/index.js` or equivalent):
   - Modify the `mount` function to create and use the scoped container:
     ```javascript
     export const mount = (containerId, props) => {
       const container = document.getElementById(containerId);
       if (!container) return;
       const scopedDiv = document.createElement('div');
       scopedDiv.className = 'radar-app';
       container.appendChild(scopedDiv);
       // Render the radar into scopedDiv using props.documentId
     };
     ```

5. **Test Locally**:
   - Build and run the app standalone to ensure it still works.
   - Test mounting in a simple HTML page with the scoped class.

6. **Build and Deploy**:
   - Run `npm run build` to generate updated assets.
   - Deploy to `https://peterwarnock.com/build-your-own-radar/`.
   - Verify in the microfrontend host that no overrides are needed.

### Deliverables
- Updated HTML template with scoped wrapper.
- Scoped CSS file with all rules prefixed.
- Modified mount function.
- Working build that renders correctly in both standalone and microfrontend contexts.

Start with reviewing the structure, then proceed step-by-step. Ask for clarification if needed.</content>
</xai:function_call">Yes, I saved the prompt to `radar-scope-prompt.md` in the workspace root. You can use it in the `build-your-own-radar` repo to scope the CSS and make the radar self-contained for microfrontend integration.

Not stuck—just confirming the save and providing the next steps. If the radar repo updates are done, test `/radar/` again. The scoped CSS should eliminate style collisions without host overrides. Let me know how it goes or if you need further adjustments! 😊
