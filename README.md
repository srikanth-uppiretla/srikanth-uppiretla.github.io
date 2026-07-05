# Engineering Portfolio — Srikanth Uppiretla

**Live site:** https://uppiretla.github.io

Personal portfolio for engineering job applications in Germany.
Dark/cream editorial design — Playfair Display serif headings, JetBrains Mono labels,
orange accent (`#f04e23`).

---

## How this repo works

| File / folder | What it is |
|---|---|
| `index.html` | **The entire website** — all text, styling and scripts in one file |
| `img/photo.jpg` | Profile photo (About section) |
| `img/` | Put project renders / screenshots here |
| `cv/Srikanth_Uppiretla_CV.pdf` | The CV behind the "Download CV" button |
| `.github/workflows/pages.yml` | Auto-deploys the site on every push — don't touch |
| `.nojekyll` | Tells GitHub to serve files as-is — don't touch |

There is **no build step**. Edit `index.html`, push, done.

---

## Making a change (the full loop)

```bash
cd C:\Users\srika\uppiretla.github.io

# 1. edit index.html in any editor (VS Code, Notepad++, ...)

# 2. check your change locally — open index.html in a browser, or:
npx serve .        # then visit http://localhost:3000

# 3. publish
git add .
git commit -m "Describe what you changed"
git push
```

The live site updates **~1 minute** after `git push`
(watch progress under the repo's **Actions** tab — green check = live).
If the browser still shows the old version, hard-refresh with `Ctrl+F5`.

---

## Where to edit what (search anchors in index.html)

Open `index.html` and search (`Ctrl+F`) for the phrase in quotes:

| To change… | Search for… |
|---|---|
| Name / role in hero | `"Srikanth<br>Uppiretla"` or `Structural Analysis Engineer` |
| Hero bottom row (Discipline/Focus/Toolchain) | `hero-meta` |
| About text | `id="about"` |
| Facts grid (location, availability, German level) | `about-facts` |
| Skills columns | `01 / Simulation` |
| Scrolling tool ticker | `marquee-track` (edit **both** copies — the text is duplicated to make the loop seamless) |
| Project cards | `id="work"` — each card is an `<article class="proj">` block |
| Experience timeline | `id="experience"` — each entry is a `<div class="tl-row">` |
| Education cards / languages | `id="education"` |
| Email / LinkedIn / GitHub / GrabCAD links | `id="contact"` |
| Accent color, fonts, spacing | `:root` at the top — all design values are CSS variables |

**Adding a new project card:** copy an entire `<article class="proj">…</article>` block,
paste it below the last one, and edit the number, tags, title and text.
The same trick works for timeline entries and education cards.

---

## Adding project images (replacing "coming soon")

1. Export/render the image — landscape 16:9, ~1200 px wide, JPEG, **under 300 KB**
   (compress at e.g. squoosh.app).
2. Save it as `img/project-name.jpg`.
3. In the project's card, replace the whole placeholder block:

```html
<!-- BEFORE -->
<div class="proj-media placeholder">
  <svg ...>...</svg>
  <span class="ph-text">FEM & geometry views — coming soon</span>
</div>

<!-- AFTER -->
<div class="proj-media">
  <img src="img/project-name.jpg" alt="Short description">
</div>
```

> ⚠ **Rocket Factory Augsburg material:** get written clearance before publishing
> any geometry, FEM plots or numbers beyond what's already in the public CV.

---

## Updating the CV PDF

Replace `cv/Srikanth_Uppiretla_CV.pdf` with the new file (same filename!), then
commit + push. Source of truth for content:
`E:\Application system\01_Master_CV\` (keep site text and CV consistent).

> ⚠ The PDF is **publicly downloadable**. Consider a portfolio version without
> home address and phone number.

---

## Remaining placeholders (to-do)

- [ ] Project images for cards 01–05 (currently "coming soon" frames)
- [ ] Card 06 — real CATIA course projects (text + images)
- [ ] GrabCAD profile link in the Contact section (search `Profile coming soon`)

---

## Troubleshooting

**Push rejected?** Someone (or another machine) pushed first — run `git pull`, then `git push` again.

**Site not updating after push?** Check the **Actions** tab on GitHub.
A red ✗ means the deploy failed — open the run to see why, fix, and push again
(or click "Re-run all jobs").

**Deploy stuck or erroring repeatedly?** This repo once had a wedged deployment;
the fix was cancelling it via API:
`gh api -X POST repos/uppiretla/uppiretla.github.io/pages/deployments/<commit-sha>/cancel`
then pushing a fresh (even empty) commit: `git commit --allow-empty -m "redeploy" && git push`.

**Want to test on your phone?** After `npx serve .`, visit
`http://<your-pc-ip>:3000` from the phone (same Wi-Fi).
