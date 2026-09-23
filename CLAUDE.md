# skyyang.net — Sky Yang's personal website

Static site. **No build step, no dependencies, no node needed.** Edit files, push, done.

## How it deploys

- Source of truth: `main` of `Wethedarkness/skyyang.net`. This repo holds ONLY the personal homepage + blog.
- Live site: Cloudflare. DNS for `skyyang.net` is on Cloudflare (registrar Hostinger). The Cloudflare Pages
  project `goodstorefront` owns the domain; its middleware proxies the personal site to the `skyyang-net`
  Pages project, which `~/.eragon/sites/skyyang-deploy.sh` deploys from this repo. GitHub Pages
  (wethedarkness.github.io/skyyang.net) still builds via `.github/workflows/static.yml` as a mirror.
- `/life` = the passphrase-locked personal dashboard (ciphertext only), auto-published by
  `memory/projects/life-dashboard/publish-web.mjs`. `/previews` and `/leads` are NOT in this repo and must never
  be added back (Sep 23 2026); they live in the goodstorefront Cloudflare project.
- Email `sky@skyyang.net` runs on Titan (MX/SPF records on Cloudflare DNS). **Never touch MX/TXT records.**

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
- Name: "Sky Yang" top line in the same body serif, 1.35rem/600, static, color --fg2 (slightly
  softer than body ink). No animation (per Sky, Aug 14).
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
