---
name: clean-separation
description: Use when writing or editing web code (HTML, CSS, JavaScript) and backend code. Keeps markup, styles and scripts strictly separated, busts caches on every change and enforces a code diet - new code in means old code out.
---

# Clean separation

Professional code has a place for everything and everything in its place.

## Structure

- **HTML is markup only.** No `<script>` blocks with logic, no `style="..."` attributes, no `<style>` tags. Scripts live in `.js` files, styles in `.css` files, loaded by reference.
- **One responsibility per file.** A module that renders a panel does not also fetch prices and write to storage.
- **Backend logic stays in the backend.** The client asks; the server decides. Never trust the client for prices, permissions or limits.

## Cache busting

Every time a CSS or JS file changes, bump its version in the place that loads it: `app.js?v=42` → `app.js?v=43`. If a module is imported by another module, bump the importer too, all the way up to the HTML. Otherwise users run a mix of old and new code and you debug ghosts.

If the site uses a service worker, bump its cache name on every deploy.

## Code diet

- **New code in = old code out.** When you replace a function, a style or a feature, delete the old one in the same change.
- No zombie CSS (rules that match nothing), no duplicate functions, no commented-out blocks "for later". Git remembers.
- No mock data, placeholder numbers or fake features left in production paths. If something is not built yet, the UI says so honestly.

## Before you finish

- Run the syntax checker for every file you touched (`node --check`, `python -m py_compile`, linters).
- Open the page and confirm nothing is loaded inline and every bumped version actually loads.
