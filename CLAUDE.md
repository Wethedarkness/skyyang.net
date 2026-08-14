# skyyang.net — Sky Yang's personal website

Static site. **No build step, no dependencies, no node needed.** Edit files, push, done.

## How it deploys

- Hosted on **GitHub Pages** from the `main` branch of `Wethedarkness/skyyang.net` (root folder).
- Every `git push` to `main` auto-deploys to https://skyyang.net in ~1 minute.
- Domain `skyyang.net` is registered at **Hostinger**; DNS A records point the apex
  at GitHub Pages (185.199.108-111.153), `www` CNAME points at `wethedarkness.github.io`.
- The `CNAME` file in this repo pins the custom domain. **Never delete it.**
- Email `sky@skyyang.net` runs on Titan Email via Hostinger MX records.
  **Never touch DNS MX/TXT records** — only A/AAAA/CNAME belong to the website.

## Workflow

```bash
# edit index.html / styles.css, then:
git add -A && git commit -m "describe change" && git push
```

Preview locally by opening index.html in a browser (it is plain HTML):
`open index.html`

## Design system (ported from neolee.xyz)

- Font: EB Garamond (Google Fonts), serif everywhere
- Colors: paper `#f0eee6` (bg), ink `#2b2620` (text), accent `#9c6b30` (link underlines), hairline `#dbd7cb`
- Layout: single centered column, max-width 42rem, generous top margin (8rem desktop)
- Links: underlined with 60% accent color, full accent on hover
- Lists: square bullets
- Keep it minimal: no nav bars, no hero images, no JS unless truly needed

## Files

- `index.html` — the entire homepage (content lives here)
- `styles.css` — design tokens + all styling
- `404.html` — not-found page
- `icon.svg` — favicon (SY monogram)
- `CNAME` — custom domain binding for GitHub Pages (do not remove)
- `.nojekyll` — tells GitHub Pages to skip Jekyll processing
