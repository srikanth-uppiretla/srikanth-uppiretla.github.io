# Engineering Portfolio — Srikanth Uppiretla

Live site: **https://uppiretla.github.io**

Single-page portfolio (CATIA V5 CAD projects + structural analysis from Master's thesis at ZARM, University of Bremen). Everything lives in one file: `index.html`.

## How to update content

Search `index.html` for `EDIT:` comments — each marks a placeholder to replace:

1. **Photo** — add `photo.jpg` (professional headshot) and replace the placeholder box in the About section with `<img src="photo.jpg" alt="Srikanth Uppiretla">`.
2. **Project cards** — replace the 4 example projects (titles, descriptions, part counts). Put renders in an `img/` folder (e.g. `img/project1.jpg`, 16:9, ~1200px wide, JPEG) and replace each `.proj-thumb` SVG placeholder with `<img src="img/project1.jpg" alt="...">`.
3. **Links** — replace the placeholder `grabcad.com` and `linkedin.com` URLs with your real profile URLs (they appear in the Projects intro, project cards, and Contact section).
4. **FEM tool** — in the Skills section, name your actual simulation tool (ANSYS / Abaqus / etc.).
5. **Languages** — set your real levels (currently guesses).
6. **Education timeline** — fill in real dates, degree names, and previous experience (bracketed placeholders).
7. **Thesis analysis image** — add a cleared result plot as `img/fea-result.jpg` **only after confirming with your supervisor what may be published**.

## Publishing changes

```
git add .
git commit -m "Update content"
git push
```

The site updates automatically within ~1 minute (GitHub Pages).

## Notes

- Keep images compressed (< 300 KB each) so the page stays fast.
- German applications: attach the PDF portfolio as an Anlage too — this site is the clickable link for CV header / LinkedIn.
- Optional: if you use this site beyond job applications, consider adding an Impressum page (German § 5 DDG requirement for business-like sites).
