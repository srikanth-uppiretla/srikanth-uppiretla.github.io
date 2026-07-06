# Engineering Portfolio — Srikanth Uppiretla

**Live site:** https://srikanth-uppiretla.github.io

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
| `certificates/` | Put recruiter-visible certificate PDFs here |
| `cv/Srikanth_Uppiretla_CV.pdf` | English CV behind the English "Download CV" button |
| `cv/Srikanth_Uppiretla_Lebenslauf.pdf` | German CV behind the German "Lebenslauf herunterladen" button |
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
| Certificate cards / PDF viewer | `id="certificates"` and `cert-viewer` |
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

## Adding certificate PDFs

Save certificate PDFs in `certificates/` using the filenames already referenced in
`index.html`:

- `certificates/german-b2.pdf`
- `certificates/msc-space-engineering.pdf`
- `certificates/bsc-mechanical-engineering.pdf`

After upload, run the site through a local server (`npx serve .`) and open the
Certificates section. Cards automatically switch from "PDF pending" to "PDF ready"
when the referenced file exists. To add another certificate, copy one whole
`<article class="cert-card">…</article>` block inside `id="certificates"`, update
the title, text and `data-pdf` filename, then place the matching PDF in
`certificates/`.

---

## Updating the CV PDF

Replace both public CV PDFs when the general CV changes, then commit + push:

- English: `cv/Srikanth_Uppiretla_CV.pdf`
- German: `cv/Srikanth_Uppiretla_Lebenslauf.pdf`

Current bilingual source:
`E:\Application system\01_Master_CV\Portfolio_General_CV_Bilingual\`.
Keep the hero, skills, experience and project wording aligned with the latest
general and daily tailored CV positioning in
`E:\Application system\04_Generated_Applications\`.

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
`gh api -X POST repos/srikanth-uppiretla/srikanth-uppiretla.github.io/pages/deployments/<commit-sha>/cancel`
then pushing a fresh (even empty) commit: `git commit --allow-empty -m "redeploy" && git push`.

**Want to test on your phone?** After `npx serve .`, visit
`http://<your-pc-ip>:3000` from the phone (same Wi-Fi).
