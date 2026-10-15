Replace the My Poker Gym logo across this site. Change ONLY logo-related markup, styles and asset files. Do not change any other text, copy, spacing or behavior. I have made manual text edits in these files that must be kept exactly as they are.

The new logo files are in the `logo-update/` folder I've put in the repo root.

## 1. Assets
- Copy `logo-update/assets/mark.svg` over `assets/mark.svg` (favicon).
- Copy `logo-update/assets/apple-touch-icon.png` over `assets/apple-touch-icon.png`.
- Copy `logo-update/assets/email-wordmark.png` into `assets/` (used by the sign-in emails).
- Delete `assets/email-logo.png` if it exists and nothing in the repo references it.
- Do NOT replace `assets/phone.webp` or `assets/table.webp` unless I say so. Updated versions with the new logo are in `logo-update/assets/` if I want them.

## 2. The old logo, and what replaces it
The old logo is a gold poker-chip SVG (`<svg class="mpg-mark" ...>`, with a `linearGradient` whose id starts with `mpgG`) followed by the text "My Poker Gym". The new logo is a single inline SVG: the full contents of `logo-update/snippets/wordmark.svg`. It already contains the words, so the separate "My Poker Gym" text next to the old mark must be removed. Keep each surrounding `<a>` element, its `href`, `class`, `id`, `title` and `aria-label` exactly as they are.

Replace it in these places:
- `index.html`: the nav logo link and the footer logo link.
- `methodology/index.html`, `about/index.html`, `terms/index.html`, `privacy/index.html`: the nav logo link (`<a class="logo" ...>`, which contains a `logo-mark` span and a `logo-text` span) and the footer logo link (`<a class="flogo" ...>`).
- `train/index.html`:
  - the header link `<a class="home-link" id="homeLink" ...>`, replacing its inner content with the wordmark SVG;
  - the footer logo link (`<a class="flogo" ...>`);
  - the `<link rel="icon" href="data:image/svg+xml,...">` tag: set `href` to the single line in `logo-update/snippets/favicon-data-uri.txt`;
  - the JavaScript function `heroAvatarSVG()`: make it return the markup in `logo-update/snippets/seat-avatar.svg` (keep it a template string).

## 3. Styles
- In the `<style>` block of `index.html` and the four content pages, append the rules from `logo-update/snippets/styles-site-pages.css`.
- In `train/index.html`, append the rules from `logo-update/snippets/styles-trainer.css` at the end of its last `<style>` block.
- Leave any old `.logo-mark` or `.logo-text` rules in place; they're harmless. Only remove them if they now visibly break something.

## 4. Check before committing
- Search all HTML files for `mpg-mark` and `id="mpgG`. There should be no matches left.
- Confirm the only lines changed are the logo markup, the favicon tag, `heroAvatarSVG()`, the appended CSS and the asset files. Run `git diff --stat` and show me `git diff` for one content page and for `train/index.html` so I can review.
- If a local preview is easy, check the header at 390px wide for horizontal overflow. If the nav overflows, reduce the logo height in the mobile rule rather than changing anything else.
- Don't commit or push until I've approved the diff.
