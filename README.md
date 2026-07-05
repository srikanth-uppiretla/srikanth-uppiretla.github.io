# Engineering Portfolio — Srikanth Uppiretla

Live site: **https://uppiretla.github.io**

Single-page portfolio in the style of a modern design-engineer portfolio: dark/cream sections,
serif display type (Playfair Display), monospace labels (JetBrains Mono), orange accent.
Everything lives in `index.html`; assets in `img/` and `cv/`.

Content source: `E:\Application system\01_Master_CV\Master_CV_English.md` (the master truth file).
When the CV changes, update both.

## Structure

- **Hero** — name, role (Structural Analysis Engineer), Download/View CV, discipline/focus/toolchain
- **About** — photo, summary, facts (location, availability, degree, German B2)
- **Skills** — "The Toolkit": Simulation & Analysis / CAD & Design / The Edge + marquee
- **Work** — 6 project cards (RFA thesis, LOX tunnel, ASTRA shell, DLR lander study, 4WS prototype, CATIA portfolio)
- **Experience** — timeline (RFA thesis, RFA internship, ASTRA e.V.)
- **Education** — M.Sc. / B.Sc. / German B2 cards + language strip
- **Contact** — email card, LinkedIn/GitHub/GrabCAD, direct-message form (opens visitor's mail client)

## Placeholders still to fill

1. **Project images** — every card has a "coming soon" placeholder. Add images to `img/`
   (16:9, ~1200px, <300 KB) and replace the `.proj-media.placeholder` div with
   `<div class="proj-media"><img src="img/xxx.jpg" alt="..."></div>`.
   ⚠ RFA project images need employer clearance before publishing.
2. **CATIA card (06)** — update text/images when the CAD course projects are done.
3. **GrabCAD link** — in Contact section, replace the "coming soon" entry once the profile exists.

## Publishing changes

```
git add .
git commit -m "Update content"
git push
```

Site updates automatically in ~1 minute (GitHub Pages).

## Notes

- `cv/Srikanth_Uppiretla_CV.pdf` is publicly downloadable — keep in mind it contains
  personal contact details; swap in a portfolio version without address/phone if preferred.
- Local preview: Claude launch config "portfolio" (npx serve, port 5544).
