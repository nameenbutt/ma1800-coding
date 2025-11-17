## Quick context

This repository is a small static HTML/CSS student project. Primary content lives in the repository root and week folders (for example `index.html`, `page-01.html`, `week-03/`, `week-05/`). There is no build system or server by default — pages are served as plain files.

## What an AI coding agent should know first

- Purpose: simple static pages and exercises. Changes should preserve the student's learning intent (avoid aggressive rewrites of HTML structure unless fixing clear errors).
- Key entry files: `index.html`, `page-01.html` (root). Weekly exercise folders: `week-03/`, `week-05/`.
- Styles: CSS files like `style.css`, `week-03/style-02.css`. Linking between HTML and CSS uses relative hrefs in the same folder.
- Images: `week-05/images/` and `week-05/images 1/` — note that some directories or filenames contain spaces which can break tooling and URLs; prefer normalized names when adding files.

## Common project patterns and gotchas (use these as rules)

- The HTML is informal and contains malformed tags (missing doctype, stray tags, incorrect comments). When editing:
  - Prefer minimal, incremental fixes that keep structure and student's content.
  - If you correct markup (e.g., add a doctype or close tags), do so consistently and in small commits with an explanation.
- CSS is applied via local stylesheet links. Use the same relative linking pattern (e.g., `<link rel="stylesheet" href="style-02.css">`) when adding styles.
- Avoid renaming or moving files without updating all relative links in the same folder.

## Developer workflows (explicit commands / examples)

There is no build system; preview and quick validation are the normal workflows.

- Quick local preview (open file in default browser on macOS):

  open index.html

- Serve a local static HTTP server (recommended for testing relative paths and images):

  # Python 3 built-in server (serves current directory on :8000)
  python3 -m http.server 8000

  # Or use a node-based live server if available (optional):
  npx live-server --port=8000

- HTML validation: run pages through the W3C/validator or visually inspect in a browser. Because markup is frequently informal, prefer targeted fixes.

## Edits, examples and patterns to follow in PRs

- When adding a new exercise page, follow the repo layout: add the HTML to the appropriate `week-XX/` folder and include a local CSS file or a link to an existing stylesheet.
- Example: adding a CSS link in `week-03/ex-02.html` uses the existing pattern:

  <link rel="stylesheet" href="style-02.css">

- When adding images, avoid spaces in file or directory names. If you must keep an original name with spaces, URL-encode or quote the path in HTML (`src="images%201/cat.png"`). Prefer renaming to `images-1/`.

## Integration & external dependencies

- External images: some HTML files reference external image sources (e.g., Unsplash URLs). These are optional and not required to run pages locally.
- No JS bundlers, package manifests, CI config, or automated tests detected. If you add automated tools, document them in the root `README.md`.

## Commit & PR guidance for automated agents

- Keep changes small and focused (one learning-fix per commit). Use descriptive commit messages like: `week-03: fix missing closing tag in ex-02.html`.
- If you fix markup across multiple files, call it out in the PR description with before/after rationale.

## Files to reference when deciding a change

- `index.html`, `page-01.html` — root entry points
- `week-03/` (includes `ex-02.html`, `style-02.css`) — shows how exercises are structured and how CSS is linked
- `week-05/` (contains `index.html` and `images/`) — example of images folder and potential filename issues

## When to ask the user

- If you need to make stylistic/formatting decisions that could change the student's intended output (for example, reorganizing folder structure, renaming image directories), ask before making the change.
- If you detect a desire to add automation (linting, formatter, live reload), propose the change and include minimally invasive steps.

---

If any of this is unclear or you'd like a different level of strictness (for example: strict HTML fixes vs. minimal-preservation), tell me which approach you prefer and I will update or iterate on the instructions.
