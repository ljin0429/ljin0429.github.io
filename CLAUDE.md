# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static academic personal website for Jongin Lim (ljin0429.github.io), forked from [Jon Barron's website template](https://github.com/jonbarron/jonbarron_website). It is hosted on GitHub Pages with no build step — changes pushed to `main` deploy immediately.

## Previewing locally

Open `index.html` directly in a browser, or run a local server to avoid CORS issues with relative paths:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

There are no dependencies, build tools, or package managers.

## Site structure

- `index.html` — the entire homepage: bio, news, research papers, patents, talks, awards. All content lives in this one file.
- `stylesheet.css` — shared styles for the homepage.
- `data/` — BibTeX `.txt` files for each paper, the CV PDF (`Jongin-CV.pdf`), and `Email.txt`.
- `images/` — paper thumbnail images and profile photos. Thumbnails are named `<ShortName>-<VENUE><YEAR>.png` (e.g., `PRIME-ICML2025.png`).
- `mipnerf/`, `mipnerf360/`, `zipnerf/` — standalone project pages (each has its own `index.html`, `css/`, `js/`, `img/`). These appear to be included from the original template and are not Jongin's papers.
- `CNAME` — currently set to `jonbarron.info` (the template author's domain); update this to `ljin0429.github.io` or the correct custom domain if one is configured.

## Adding a new paper

Each paper is an HTML `<tr>` block inside the research `<tbody>` in `index.html`. The pattern for a first-author (highlighted) paper:

```html
<tr bgcolor="#ffffd0" id="ShortName-venue2025">
  <td style="padding:16px;width:20%;vertical-align:middle">
    <img src="images/ShortName-VENUE2025.png" alt="Thumbnail" style="width: 160px; height: auto;">
  </td>
  <td style="padding:8px;width:80%;vertical-align:middle">
    <a href="PAPER_URL">
      <span class="papertitle">Full Paper Title</span>
    </a>
    <br>
    <strong>Jongin Lim</strong>, <a href="COAUTHOR_SCHOLAR_URL">Coauthor Name</a>
    <br>
    <em>VENUE</em>, 2025
    <br>
    <a href="data/ShortName-VENUE2025.txt">bibtex</a>
    / <a href="CODE_URL">code</a>
    <p></p>
    <p>One-paragraph description.</p>
  </td>
</tr>
```

- Omit `bgcolor="#ffffd0"` for non-first-author papers (rows without the yellow highlight).
- Add the matching BibTeX file at `data/ShortName-VENUE2025.txt`.
- Add the thumbnail image at `images/ShortName-VENUE2025.png` (160×125px is the common size for fixed-height thumbnails; use `height: auto` for variable-height ones).
- Add an `id` attribute to the `<tr>` if the paper is referenced from the News or Research sections via anchor links (e.g., `href="#ShortName-venue2025"`).
