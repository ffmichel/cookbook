# Cookbook

This folder is a recipe cookbook AND a website, published via GitHub Pages.

## Structure

- Each top-level folder is a category (e.g. `Cakes/`, `NinjaCreami/`) and appears in the site navigation.
- Recipes are markdown files inside category folders. Nested subfolders are allowed and render as nested nav sections.
- `index.html` is the website app — it reads the repo file tree at load time. Do not edit unless changing the site itself.
- `CLAUDE.md` and `README.md` files are hidden from the website.

## Workflow for adding or editing recipes

1. Add or edit `.md` files in the appropriate category folder (create new folders for new categories).
2. Filenames: lowercase snake_case, e.g. `chocolate_chip_cookies.md`. The site prettifies them for display.
3. Each recipe starts with a `# Title` heading; use tables for ingredients (see existing recipes as templates).
4. Publishing: the folder is mirrored to https://github.com/ffmichel/cookbook (site: https://ffmichel.github.io/cookbook/). A push token (expires Oct 9, 2026, Contents-RW on that repo only) is in the git-ignored `.github_token` file. Sync the folder to a clone, then commit and push:
   ```
   git add -A && git commit -m "Add <recipe>" && git push
   ```
   The site updates immediately — no build step.

## Category-specific rules

- `NinjaCreami/CLAUDE.md` has ice-cream preferences (no protein powder, no pudding mix, store-bought style).
