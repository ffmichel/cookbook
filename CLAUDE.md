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
4. Publishing: commit and push to `main` of https://github.com/ffmichel/cookbook (site: https://ffmichel.github.io/cookbook/). The site updates immediately — no build step. See "Publishing from a Claude session" below for how.

## Before writing a recipe

- This repo is the source of truth. The claude.ai Cookbook Project's doc list holds only a few recipes and is not a mirror of the repo, so never conclude a recipe is missing because it is not in the Project docs.
- List the repo first (`git ls-files`). The repo is public, so a read-only clone works from any session.
- Check `Pastry/` for an existing base recipe (crust, cream) and link to it rather than writing a new one. Example: a recipe calling for pâte sucrée or pâte brisée uses `Pastry/pate_brisee_sucree.md`.
- Copy the format of an existing recipe in the same category (e.g. `Pies/pumpkin_pie.md`).

## Publishing from a Claude session

There are two routes. Use whichever the session has; lacking one of them does not mean the recipe can't be published.

- **Cloud session (claude.ai on the web or phone, no Desktop Commander):** the GitHub connection has push access to this repo. Attach `ffmichel/cookbook` with push access, clone it, commit, and push to `main`. If attaching with push access is refused, tell Fabrice that and ask him to confirm, instead of reporting that publishing is impossible.
- **Mac session with Desktop Commander:** work in `~/claude/cookbook` (SSH remote, no token needed) and run one command:
  ```
  cd ~/claude/cookbook && git pull --rebase && git add -A && git commit -m "Add <recipe>" && git push 2>&1 | tail -5
  ```

In both cases:

- Commit straight to `main`; no branches or pull requests.
- Always pass `-m` to `git commit`, so nothing opens an editor.
- Commit as `Fabrice Michel <12208187+ffmichel@users.noreply.github.com>`, set repo-locally in the clone (`git config user.name` / `git config user.email`).
- Saving a recipe to the Project docs does not publish it. Only a push to this repo does.

## Linking between recipes

- Base recipes (a crust, a pastry cream) live in their own file so other recipes can reuse them.
- Link with a normal markdown link, relative to the current file:
  - same folder: `[Pâte brisée sucrée](pate_brisee_sucree.md)`
  - another category: `[Pâte brisée sucrée](../Pastry/pate_brisee_sucree.md)`
- The site turns relative `.md` links into in-site routes; the same links work when browsing the repo on GitHub.
- In an ingredient table, put the link in the Ingredient cell and the weight needed in the Amount cell, e.g. `| [Pâte brisée sucrée](../Pastry/pate_brisee_sucree.md) | 385 g |`.

## Category-specific rules

- `NinjaCreami/CLAUDE.md` has ice-cream preferences (no protein powder, no pudding mix, store-bought style).
