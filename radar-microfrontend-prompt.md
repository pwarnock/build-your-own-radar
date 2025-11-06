**Prompt for AI Assistant in `pwarnock/build-your-own-radar` Repo:**

You are an AI coding assistant working on the `pwarnock/build-your-own-radar` repository, which is a fork of ThoughtWorks' `build-your-own-radar` project. This is a React-based SPA for visualizing technology radar data. The goal is to refactor it into a microfrontend module using Webpack Module Federation, so it can be remotely loaded and mounted into another application (the main Hugo site at `pwarnock.github.io`).

### Context
- The radar app currently runs as a standalone SPA, accepting a `documentId` URL parameter for JSON data.
- We need to expose it as a federated module named `radarRemote`, allowing the main site to load and mount it dynamically (e.g., via `<div id="radar-container"></div>`).
- Default data URL: `/tools/index.json` (relative to the consuming site's origin).
- Host the built module on GitHub Pages or a CDN for easy consumption.

### Requirements
- Use Webpack Module Federation to expose the app as a remote module.
- Modify the app to accept `documentId` via props instead of URL params.
- Ensure the module exports a mount function that can render into a provided DOM element.
- Add error handling and loading states.
- Set up a GitHub Actions pipeline for build and deployment.
- Keep the app iframe-friendly (no routing conflicts).
- Test locally and ensure compatibility with the main site's data format (an array of radar entries).

### Steps to Implement
1. **Audit Current Setup**:
   - Review `package.json`, `webpack.config.js`, and the app's entry point (e.g., `src/index.js`).
   - Confirm React version and dependencies.

2. **Install Dependencies**:
   - Add `@module-federation/webpack` if not present.

3. **Update Webpack Config for Federation**:
   - Configure as a "remote" module.
   - Expose the main app component (e.g., `export default App` or a custom mount function).
   - Set `library` type to `var` or `umd` for broad compatibility.

4. **Refactor App Entry**:
   - Change from reading `documentId` from URL to accepting it as a prop.
   - Export a function like `mount(containerId, props)` that renders the app into the specified element.

5. **Build and Test**:
   - Build the remote module.
   - Test mounting in a simple HTML page with a mock `documentId`.

6. **Set Up CI/CD**:
   - Create `.github/workflows/deploy.yml` to build on push and deploy to GitHub Pages.
   - Ensure `remote-entry.js` is accessible (e.g., at `https://pwarnock.github.io/build-your-own-radar/remote-entry.js`).

7. **Documentation**:
   - Update README with usage instructions for consuming apps.

### Deliverables
- Updated `webpack.config.js` with federation config.
- Refactored app entry point.
- Working build output.
- GitHub Actions workflow.
- Test HTML page demonstrating the module.
- Brief README section on integration.

Start with auditing the current setup, then proceed step-by-step. Ask for clarification if needed.
