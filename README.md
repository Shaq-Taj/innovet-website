# InnoVet DMAP website: Challenge Coin

Marketing site for **DMAP**, InnoVet's platform for managing contracts, contractor personnel, documents, and administrative workflows. The homepage features an interactive 3D InnoVet seal ("challenge coin") that visitors can drag or use the arrow keys to spin.

It is a static site: plain HTML and CSS, with no build step and no server code.

## View it locally

You need a browser and any static file server. With Python, which is preinstalled on macOS:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

Alternatively, with Node.js installed:

```bash
npx serve .
```

Use a server rather than double-clicking the files, so links, fonts and the 3D coin behave the same way they will online. The homepage loads React, htm, three.js and Google Fonts from public CDNs, so you also need an internet connection.

## Pages

| File | Page |
|---|---|
| `index.html` | Home: 3D seal, headline, overview, capabilities, how it works |
| `about.html` | Purpose, who DMAP supports, benefits |
| `capabilities.html` | The six core capabilities |
| `faqs.html` | Frequently asked questions |
| `careers.html` | Careers, with the **Apply here** button |
| `jobs.html` | Job openings search page (currently shows "no current openings") |
| `contact.html` | Request a demo and contact details |
| `site.css` | Shared styles for every page except the homepage, which has its own styles inline |

## Editing

- **Text and layout:** edit the `.html` files directly. Every page repeats the same header and footer, so a change to navigation or contact details has to be made in each file.
- **Homepage:** `index.html` is a single file containing its styles and a script.
  - The page content is written as React components in the script, in the `COMPONENTS` section.
  - The 3D seal is in `CoinRig`. Its artwork (rope border, lettering, stars, laurels, ribbon) is drawn in `sealArt()`.
- **Job openings:** to list a real opening, replace the "There are no current openings" panel in `jobs.html` with job cards, and update the `0` counts.
- **Forms:** this version has no server, so "Request a Demo" and "Apply here" use email links to dmap@innovetusa.com, plus copy-to-clipboard buttons.

## Brand rules

- Light pages in red, white and blue: navy `#14245C`, blue `#2E4E8C`, red `#B22234`, with pale tints `#F4F7FC`, `#EAF0FA` and `#FBEDEF`. No dark backgrounds.
- Use the InnoVet SVG logo, already inlined in each page header and footer: navy "INNO", red striped "VET", with the star on the V.
- The favicon is the InnoVet "V", embedded in each page as a data URI.

## Accessibility (Section 508 / WCAG 2.1 AA)

Every page passes an automated axe-core scan at desktop and 320px widths. When you add content, keep these in place:

- the "Skip to main content" link, and `<main id="main">`
- exactly one `<h1>` per page, with heading levels in order
- visible focus outlines, and keyboard access to every control (the menu closes with Escape)
- `aria-hidden="true"` on decorative icons and stars
- text contrast of at least 4.5:1
- support for "reduce motion": the coin's idle spin also stops on its own after 5 seconds

Before launch, also test with a real screen reader (VoiceOver on Mac, NVDA on Windows) and at 200% zoom.

## Publish on GitHub Pages

1. In this repository, go to **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**, then select the **main** branch and the **/ (root)** folder, and click **Save**.
3. After a minute or so, the site is live at `https://shaq-taj.github.io/innovet-website/`.

The empty `.nojekyll` file tells GitHub Pages to serve the files exactly as they are. Note that this repository, and therefore the site, is public if Pages is enabled on a public repository.

## Contact

dmap@innovetusa.com · +1 (703) INNOVET · 3500 S Dupont Hwy, Dover, DE 19901
