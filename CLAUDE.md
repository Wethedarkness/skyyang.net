# skyyang.net — Sky Yang's personal website

Static site. **No build step, no dependencies, no node needed.** Edit files, push, done.

## How it deploys

- Hosted on **GitHub Pages** from the `main` branch of `Wethedarkness/skyyang.net` (root folder).
- Every `git push` to `main` auto-deploys to https://skyyang.net in ~1 minute.
- Domain `skyyang.net` is registered at **Hostinger**; apex ALIAS + `www` CNAME point at
  `wethedarkness.github.io`.
- The `CNAME` file in this repo pins the custom domain. **Never delete it.**
- Email `sky@skyyang.net` runs on Titan Email via Hostinger MX records.
  **Never touch DNS MX/TXT records** — only A/AAAA/CNAME belong to the website.

## Workflow

```bash
# edit files, then:
git add -A && git commit -m "describe change" && git push
```

Preview locally by opening index.html in a browser: `open index.html`

## Design system (v2 — "Thinking Machines" style, current)

Ported from thinkingmachines.ai:

- Background: white. Text: `#282828` (`--fg`), grays `--fg1..--fg5`.
- Body: **Iowan Old Style** (macOS system font) / Georgia serif, 17px, line-height 1.6.
- Name: "Sky Yang" top line in the same body serif, 1.3rem/600 (neolee-style placement) with an
  animated gradient shimmer (background-clip: text + gradShift keyframe) + gentle float (.site-name).
- Nav: fixed top bar, right-aligned sans links (15px): Main, Blog.
- Content column: 660px (`--content-max`), centered.
- Links: underlined with 30% gray decoration, darken on hover.
- "NEW" pill + announcement line under the hero wordmark (`.home-announcement`).

## Pages

- `index.html` — homepage (hero wordmark + bio)
- `blog/index.html` — blog catalog, currently empty. To add a post:
  1. Create `blog/my-post/index.html` (copy blog/index.html structure, put content in the article)
  2. Add `<li><a href="/blog/my-post/">Title</a><span class="post-date">Mon YYYY</span></li>`
     to the `.post-list` in `blog/index.html` and remove the `.empty-state` paragraph.
- `404.html` — not-found page

## Rollback to v1 (neolee.xyz style)

The previous cream/EB Garamond version is preserved as git tag `v1-neolee-style`
(also branch `neolee-style`). To roll back the look:

```bash
git checkout v1-neolee-style -- index.html styles.css 404.html
git rm -r --cached blog && rm -rf blog   # v1 had no blog
git commit -m "roll back to v1 neolee style" && git push
```

Or to just compare: `git diff v1-neolee-style -- styles.css`
