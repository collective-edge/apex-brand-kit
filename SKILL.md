---
name: apex-brand-guidelines
description: Applies Apex Paramedics' brand standards — navy-blue + gold color palette, Montserrat typography, and logo usage — to ANY output representing Apex Paramedics. Use whenever generating Apex Paramedics materials of any kind: emails, social posts, slides, documents, web content, marketing collateral, internal comms, training materials, flyers, letters, one-pagers, tables, or any visual artifact. Also use when reviewing existing materials for brand compliance.
---

# Apex Paramedics — Brand Guidelines

**When to apply:** Whenever creating or reviewing any material that represents Apex Paramedics, in any medium (digital or print, formal or casual). This skill defines the look-and-feel; specific layouts and templates are intentionally not prescribed here so the brand can apply across many formats.

## CRITICAL: Asset loading

**This brand kit is cloud-hosted.** All fonts and logos live on a public CDN (jsDelivr, backed by GitHub) so any Claude session anywhere can pull them down. **Do not look for local files.** Use the URLs below directly in generated HTML, CSS, or markdown.

**Base CDN URL:**
```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/
```

**Specific asset URLs (copy these into outputs):**

| Asset | URL |
|---|---|
| Montserrat (variable TTF) | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf` |
| Horizontal logo (color) | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-color.svg` |
| Horizontal logo (white) | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg` |
| Mark / arc only (color) | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/mark-color.svg` |
| Mark / arc only (white) | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/mark-white.svg` |
| Brand colors (JSON) | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/colors.json` |

A raster `horizontal-color.png` is also available for contexts that require a bitmap. The authoritative vector source is `assets/logos/source/apex-paramedics.eps`.

**Drop-in base CSS** (includes @font-face for Montserrat + brand CSS variables):
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/brand-base.css">
```

**For PDF rendering (weasyprint, wkhtmltopdf, Chrome print):** always include the @font-face declaration so the font is embedded in the output PDF. Use this minimal block at the top of any HTML you intend to print:

```css
@font-face {
  font-family: 'Montserrat';
  src: url('https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf') format('truetype');
  font-weight: normal;
}
@font-face {
  font-family: 'Montserrat';
  src: url('https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf') format('truetype');
  font-weight: bold;
}
body { font-family: 'Montserrat', Calibri, Arial, sans-serif; }
```

---

## 1. Brand Colors

Apex Paramedics uses a **navy-blue + gold** palette drawn straight from the logo (Pantone Blue 072 C wordmark, Pantone 1235 C arc). Blue is the foundation; gold is the signature accent. Every piece of collateral should draw from these colors exclusively — never introduce off-brand hues.

| Name          | Hex       | RGB              | Usage                                                                 |
|---------------|-----------|------------------|------------------------------------------------------------------------|
| Apex Blue     | `#134891` | 19, 72, 145      | Primary brand color — logo wordmark, headers, links, buttons, accents  |
| Apex Blue Deep| `#0E3468` | 14, 52, 104      | Hero backgrounds, full-width header bands, section dividers, footers    |
| Apex Blue Light| `#95ADCE`| 149, 173, 206    | Tertiary accents, hover states, lighter highlights                      |
| Apex Gold     | `#FFC92B` | 255, 201, 43     | Signature accent — the arc, accent bars, kickers, stat numerals         |
| Apex Gold Deep| `#B98900` | 185, 137, 0      | Text-safe gold for small/bold labels or icons on white                  |
| Black         | `#000000` | 0, 0, 0          | Body text, high-contrast headings on light backgrounds                  |
| White         | `#FFFFFF` | 255, 255, 255    | Text on dark backgrounds, page background                               |

### Color usage rules

- **Apex Blue (#134891)** is the dominant brand color and the default for headers, links, buttons, column headers, and accent bars.
- **Apex Blue Deep (#0E3468)** anchors large dark areas: hero/title bands, full-width strips, footers, section dividers.
- **Apex Gold (#FFC92B)** is the signature accent — echo the logo's arc. Use for kicker lines, thin accent rules under headers, stat numerals, highlight underlines, and to draw the eye. Use it as a **highlight, not a background for large areas** — it vibrates at scale.
- **Gold as text:** bright gold `#FFC92B` fails contrast on white. For gold text/small labels on white, use **Apex Gold Deep `#B98900`**, and only at bold/large sizes. Default body/heading text to blue or black.
- **Apex Blue Light (#95ADCE)** is for tertiary accents and hover states only — never a large-area background.
- **Backgrounds:** White is primary. For subtle alternating rows, callouts, or backgrounds, use the very light blue tint `#f2f6fc` — never anything stronger.
- **Text contrast:** White text on Apex Blue / Blue Deep. Black or Apex Blue text on white. Never Blue Light text on white — insufficient contrast.
- **No off-brand colors for decorative purposes.** Functional/data colors (chart series, status indicators) should stay within or harmonize with the blue/gold palette wherever possible.

### Extended palette (functional roles in diagrams, status, dashboards)

These are NOT primary brand colors but are official conventions for diagrams (flowcharts, dashboards, process docs) where additional roles are needed beyond the blue/gold palette. Apply consistently — do not invent new hues for these roles. Note: **gold is a brand accent, not a status color** — use the orange below for warnings so gold stays reserved for brand highlights.

| Role             | Hex       | Border    | Use                                                 |
|------------------|-----------|-----------|-----------------------------------------------------|
| Decision / query | `#4a8e3a` | `#3a7029` | Decision boxes, questions, branch points            |
| Warning / callout| `#f57c00` | `#cc6600` | Warning boxes, advisories, "watch out" pills        |
| Info / process   | `#3e3e3e` | `#2a2a2a` | Neutral process steps, context boxes                |

Color does the differentiation work — all diagram shapes should be **rectangles with small rounded corners (radius ~6px)**. Role is communicated by fill color, not by shape.

---

## 2. Logo

### Logo files (CDN URLs above)

- **Horizontal logo** — primary lockup (navy "APEX PARAMEDICS" wordmark under the gold arc). Default for most contexts.
- **Mark (arc)** — the gold arc icon alone, for compact contexts (favicons, badges, social avatars, table corners) where it reads on its own.

Color variant for light backgrounds; white variant (white wordmark, gold arc retained) for dark backgrounds.

### Logo specifications

- **Horizontal viewBox:** `63 40 1992 888` (aspect ≈ 2.24 : 1)
- **Mark viewBox:** `99 40 1803 635`
- **Colors:** Apex Blue `#134891` wordmark, Apex Gold `#FFC92B` arc; on dark, white wordmark + gold arc.
- The SVGs are traced from the Apex artwork; `assets/logos/source/apex-paramedics.eps` is the authoritative source for any future re-export.

### Usage rules

1. **Default to the horizontal logo** for any context with horizontal room. Use the arc-only mark only where space requires it (small icons, badges).
2. **Minimum clear space:** Maintain padding around the logo equal to at least the height of the gold arc on all sides.
3. **On dark backgrounds:** Use the `*-white.svg` variant (white wordmark, gold arc). Do not apply CSS filters to recolor — use the correct file.
4. **On white/light backgrounds:** Use the color variant.
5. **Minimum size:** Never render the horizontal logo smaller than ~110px wide on screen or 1 inch in print. The arc-only mark can go down to ~32px.
6. **Do NOT:**
   - Stretch, skew, or rotate the logo
   - Place the logo on busy photographic backgrounds without a solid backing
   - Change the logo colors to anything other than Apex Blue + Apex Gold (or white + gold on dark)
   - Add drop shadows, glows, outlines, or gradients to the logo
   - Separate the wordmark from the arc in the horizontal lockup
7. **Embedding:** Reference the logo URL directly with `<img src="...">` — it's a public CDN, no auth needed.

---

## 3. Typography

**Montserrat is the brand font for every output.** No exceptions. (This is the same font used across all Collective Edge operating companies — Apex, Royal, and CE itself — so only color and logo distinguish the brands.)

- Title bands / hero headlines: **800 weight, ALL CAPS, +1.5 letter-spacing**
- Section headers: **700 weight**, normal case or all caps
- Body: **500 weight** (Medium) on light backgrounds, **400** (Regular) for long-form
- Tiny labels / kickers: **800 weight, ALL CAPS, +2 letter-spacing**, often in Apex Gold Deep or Apex Blue

**Always include the @font-face declaration** at the top of any generated HTML, even if Montserrat is installed on the rendering machine. This guarantees consistent rendering and embeds the font in any downstream PDF. See the asset-loading section above for the snippet.

---

## 4. Layout conventions (Apex house style)

Blue is the structure; gold is the spark. Pattern-match these visually for new collateral.

### Header band
- Full-width strip across the very top of the page.
- Background: Apex Blue Deep `#0E3468` (optionally a subtle gradient to Apex Blue `#134891` on the right).
- **Gold accent rule:** a 3px Apex Gold `#FFC92B` line along the bottom edge of the band — echoes the logo arc.
- White Apex horizontal logo top-right (~1.4–1.8in wide) — on a white chip if only the color raster is available.
- Title text top-left: white, Montserrat 800, ALL CAPS, 18–22pt for one-pagers / 32–44pt for slides.

### Sub-banner (optional)
- Thin Apex Blue `#134891` strip just below the header band.
- White Montserrat 600, 8–9pt, ALL CAPS, +2.5 letter-spacing.
- Used for kicker / partner / category line.

### Flowchart nodes
- All node shapes are rounded rectangles (radius 6px).
- **Standard step:** Dark gray `#3e3e3e`, white ALL-CAPS Montserrat 800, optional muted subtitle below.
- **Action / highlight step:** Apex Blue `#134891`, same text treatment.
- **Decision:** Green `#4a8e3a` pill (border-radius 999px), white ALL-CAPS Montserrat 800.
- **Warning / critical:** Orange `#f57c00`, white ALL-CAPS Montserrat 800.
- **Branch labels (YES / NO):** White box with colored border matching the branch outcome.
- Connector lines: `#3e3e3e`, 1.8pt stroke, with arrow markers.

### Stat / metric callouts
- Big number: Montserrat 800, 36–60pt, Apex Blue `#134891` (or Apex Gold `#FFC92B` on a dark background).
- Unit label: Montserrat 500, 10pt, Muted.
- Kicker above: Montserrat 800, 8pt, ALL CAPS, Apex Gold Deep `#B98900`, +2 letter-spacing.

### Tables
- Header row: `#0E3468` (Apex Blue Deep) fill, white Montserrat 800 ALL CAPS 9pt.
- Body rows: white, alternating with `#f2f6fc` if alternation helps readability.
- Hairline borders: `#E2E8F0`.

### Footer
- Slim full-width footer.
- Top border: `#E2E8F0` hairline (or a 2px Apex Gold rule for a branded finish).
- Left: "Apex Paramedics | {Document Title}" in `#64748B` Muted.
- Right: revision marker (e.g., "Rev. 07.26") in Apex Blue `#134891`, Montserrat 700.

---

## 5. Quick-reference snippets

**Header band (drop-in HTML):**
```html
<header style="background:#0E3468; color:#FFFFFF; padding:0.32in 0.5in; display:flex; align-items:center; justify-content:space-between; font-family:'Montserrat',sans-serif; border-bottom:3px solid #FFC92B;">
  <div style="font-weight:800; font-size:18pt; letter-spacing:1.5px; text-transform:uppercase;">YOUR TITLE</div>
  <img src="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg" style="width:1.6in;" alt="Apex Paramedics">
</header>
```

**Sub-banner:**
```html
<div style="background:#134891; color:#FFFFFF; padding:6px 0.5in; font:600 8.5pt 'Montserrat'; letter-spacing:2.5px; text-transform:uppercase;">
  KICKER / PARTNER / CATEGORY
</div>
```

**Footer:**
```html
<footer style="border-top:1px solid #E2E8F0; padding:6px 0.5in; font:400 8pt 'Montserrat'; color:#64748B; display:flex; justify-content:space-between;">
  <span>Apex Paramedics &nbsp;|&nbsp; Document Title</span>
  <span style="font-weight:700; letter-spacing:1.5px; color:#134891;">Rev. MM.YY</span>
</footer>
```

---

## 6. Versioning

Pinning to `@main` always serves the latest version. To pin to a stable release, replace `@main` with a tag, e.g. `@v1.0`. Bump tags when you make breaking changes (logo redesign, color shifts).

---

## 7. Confirm before shipping

When you finish an Apex deliverable, state which brand choices you applied (which logo variant, primary accent, font embedding method) so the user can verify at a glance.
