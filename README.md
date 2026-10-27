# Cortex client portal — static prototype

A clickable picture of the portal. One HTML file, no build step, no backend. Nothing is wired up: the sign-in, Publish, and import buttons show a "prototype" note. The Oct 22 Data Centers Work edition is the only real PDF; the rest are placeholders.

## Put it on GitHub Pages (about 3 minutes)

1. Create a new repository on GitHub, e.g. `cortex-portal-prototype`. Private is fine if your account is on GitHub Pro/Team; otherwise it must be public for Pages to work on the free plan. Nothing in here is sensitive except the sample PDF — delete `assets/newsletters/` and set `pdf:false` on the Oct 22 edition in `index.html` if you need the repo to be public and don't want the newsletter visible.
2. Upload everything in this folder to the repo (drag the files onto the GitHub page, or `git init && git add . && git commit -m "Prototype" && git push`). Keep `.nojekyll` — it's a hidden file.
3. In the repo: Settings → Pages → Build and deployment → Source: "Deploy from a branch" → Branch: `main`, folder `/ (root)` → Save.
4. Wait a minute. Your site is at `https://<your-username>.github.io/cortex-portal-prototype/`.
5. Share these links with the team:
   - Sign-in screen: `.../#login`
   - Edition view (the core screen): `.../#edition/dcw-daily/2026-10-22`
   - Archive: `.../#archive/dcw-daily`
   - Cortex staff view: `.../#admin/upload`

When IT gives you DNS for prcortex.com, add a `CNAME` file containing `portal.prcortex.com` and point a CNAME record at `<your-username>.github.io`.

## Editing the picture

Everything is in `index.html`:
- Colors and fonts: the `:root` block at the top of `<style>`. Swap the hex values for the ones in the prcortex.com site.
- Editions shown in the archive and home: the `EDITIONS` array near the top of `<script>`.
- The "On the radar" numbers: the `ANALYTICS` object.
- Client and publication names: `CLIENT` and `PUBS`.
- To add another real PDF: drop it in `assets/newsletters/`, add `pdf:true` to that edition, and point `PDF_URL` logic at it (currently one PDF is shared).

## From prototype to real

This is the "picture." The buildable spec, data model, and Claude Code prompts are in the separate `cortex-portal-kit` folder — the prototype's screens map one-to-one onto SPEC.md §5.
