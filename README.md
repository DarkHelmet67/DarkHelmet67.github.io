# Luca Ceccatelli — personal site

Personal site served by GitHub Pages at https://darkhelmet67.github.io/

## Files

| Path | What it is |
| :-- | :-- |
| `index.html` | Home page, hand-written HTML (no build step, no dependencies) |
| `cv/` | CV in English and Italian (PDF) |
| `claude-cheatsheet.md` | Claude commands cheat sheet, the source of the page [`claude-cheatsheet.html`](https://darkhelmet67.github.io/claude-cheatsheet.html) |
| `_templates/page.html` | Pandoc template used to turn Markdown files into HTML pages |
| `.github/workflows/pages.yml` | Workflow that builds and publishes the site |
| `.nojekyll` | Turns off Jekyll: the site is published as-is |

## How publishing works

Every push to `main` runs the **Pubblica sito** workflow (GitHub Actions):

1. copies the repository into a `_site/` folder, leaving out `.git`, `.github` and `_templates`;
2. converts every `.md` file in the root, except this README, into an `.html` page with Pandoc and the `_templates/page.html` template;
3. publishes `_site/` to GitHub Pages.

The generated HTML is **not committed** to the repository: it only exists in the published site, so the Markdown file stays the single source. To update a page, edit its `.md` and push.

To add a new page, create a `.md` file in the root: after the push it will be published as `<name>.html`. The page title comes from the first `# ` heading.

Requirement: *Settings → Pages → Source* must be set to **GitHub Actions**.
