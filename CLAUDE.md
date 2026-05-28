# CLAUDE.md — Emre Işık's research website

## Site structure

Jekyll (Minima theme), deployed via GitHub Pages at `https://emre-isik.github.io`. Working branch is `main`. Always pull before starting work; push when done.

**Pages:**
- `index.markdown` — home page (layout: home)
- `about.markdown` — biography
- `Stellar.markdown` — stellar magnetic activity nuggets (`/Stellar/`)
- `Solar.markdown` — solar magnetic activity nuggets (`/Solar/`)
- `Astrobiology.markdown` — astrobiology nuggets (`/Astrobiology/`)
- `Teaching.markdown` — courses

**Assets:** `assets/images/[PageName]/filename.png` — e.g., `assets/images/Stellar/rot-B.png`

## ingest_local/

Drop zone for PDFs, TeX files, and images to be processed. Scan at the start of every nugget task. Never committed to git (gitignored). Files are ephemeral — drop, process, done.

## Research nuggets

Each research page lists results in reverse chronological order, separated by `---`. Format:

```markdown
### **Descriptive title of result (YEAR)**

<img src="/assets/images/[Page]/filename.png" alt="filename.png" width="700">
<p style="background-color: #f0f0f0; margin: 0; padding: 5px; font-size: 0.9em; text-align: left;">
Caption text.
</p>

Plain-language description. **Key novelty in boldface.** 1–2 paragraphs.

**Reference**

Author1, A., Author2, B., **Işık, E.** **YEAR**, Title of paper, [*Journal* Vol, Page](DOI)
```

**Year in section header:** use arXiv/submission year, which may differ from formal publication year.

**"In review" / "New papers" blocks:** visible while the paper is under review; remove block and convert to a full nugget once accepted.

### Image widths
- 700 px — single figure at full text width
- 350–450 px — side-by-side pair or floated image with text wrap
- 250 px — small inset

### Caption styles
- **Gray box** `<p style="background-color: #f0f0f0; margin: 0; padding: 5px; font-size: 0.9em; text-align: left;">` for standalone captions below images (Stellar.markdown style)
- **Float + figure-caption class** `<div style="float: left/right; ..."><img ...><p class="figure-caption">...</p></div>` when text wraps around image (Solar.markdown style)

## Reference format

```
Author1, A., Author2, B., **Işık, E.** **YEAR**, Title of paper, [*Journal* Vol, Page](DOI)
```

- Year in **bold** immediately after the author list, followed by a comma
- **Işık, E.** always bolded
- Paper title in plain text, before the linked journal citation
- For accepted/not yet published: `[*Journal*, accepted](ADS or arXiv URL)`

## PDF figure extraction

Tools available: `pdfimages`, `pdfcrop`, `gs` (Ghostscript), `convert` / `magick` (ImageMagick).

Extract a single page as PNG (300 dpi):
```bash
gs -dNOPAUSE -dBATCH -sDEVICE=png16m -r300 -dFirstPage=N -dLastPage=N \
   -sOutputFile=fig.png input.pdf
```
Then auto-crop whitespace: `magick fig.png -trim output.png`

## Author name

Emre Işık — special characters: ş (s-cedilla), ı (dotless i). In markdown/HTML write `Işık` directly (UTF-8). In LaTeX: `I\c{s}{\i}k`.
