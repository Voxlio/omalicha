# Happy Birthday, My Omalicha

A single-page birthday letter with music, confetti, and a staggered reveal.
Static site, no build step — GitHub Pages serves it as-is.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The whole page: markup, styles, and script |
| `happybirthday.mp3` | Background music, toggled by the floating button |
| `favicon.ico` | Root-level icon (browsers request this path by default) |
| `site.webmanifest` | Install metadata for "Add to Home Screen" |
| `assets/favicon.svg` | Vector icon, preferred by modern browsers |
| `assets/favicon-16x16.png`, `-32x32`, `-48x48` | Raster tab icons |
| `assets/apple-touch-icon.png` | iOS home-screen icon (180px) |
| `assets/icon-192.png`, `icon-512.png`, `icon-512-maskable.png` | Android / PWA icons |
| `assets/og-image.png` | 1200×630 link preview card |

The icons are the "O" from the OMALICHA wordmark, drawn as a ring so it stays
legible down to 16px — the full wordmark is far too wide to read in a browser tab,
so it lives on the link preview card instead, where it has room.

## Publish to GitHub Pages

Live URL: <https://voxlio.github.io/omalicha/>

The site URL is already stamped into the `og:`/`twitter:` link-preview tags, and
`origin` is already set to `https://github.com/Voxlio/omalicha.git`. So:

1. Create the **public** repo `omalicha` on GitHub if it doesn't exist yet. Don't
   let GitHub add a README or `.gitignore` — this folder already is the repo.
2. From this folder:

```bash
git push -u origin main
```

3. On GitHub: **Settings → Pages → Source: Deploy from a branch**, branch `main`,
   folder `/ (root)`. Save.
4. Wait about a minute, then open <https://voxlio.github.io/omalicha/>.

Pages is only free on public repos. If the repo is private, Pages needs a paid plan.

If the repo name or owner ever changes, the preview URLs in `index.html` must be
updated too (three occurrences), or shared links will show a broken image:

```bash
sed -i 's|https://voxlio.github.io/omalicha|NEW_URL|g' index.html
```

## Notes

- **The card photo** loads from `i.ibb.co`, a free image host. If that link ever
  dies the card falls back to a solid deep brown and the letter stays readable.
  To remove the dependency entirely, save the photo as `assets/photo.jpg` — the
  CSS already prefers a local copy over the remote one, no edit needed.
- **Music won't autoplay** on its own; browsers block that. It starts when the
  "Open Birthday Letter" button is tapped, which counts as user intent.
- **Testing a link preview:** WhatsApp and Facebook cache aggressively. If the
  preview looks wrong after you fix something, clear it at
  <https://developers.facebook.com/tools/debug/>.
