# Apex Paramedics · brand reference

Everything about this brand that does not belong in `SKILL.md`. Read on demand.

Apex Paramedics is an operating company under Collective Edge. Palette and logo are the only things that vary between brands in the house. Type is shared and lives in `reference/type-system.md`.

---

## 1. Palette

The palette is drawn straight from the mark. The wordmark is Pantone Blue 072 C. The arc is Pantone 1235 C. Blue is the foundation, gold is the signature accent. Never introduce a hue that is not on this page.

### Brand

| Name | Variable | Hex | RGB | Usage |
|---|---|---|---|---|
| Apex Blue | `--apex-blue` | `#2B338D` | 43, 51, 141 | Primary brand color. Logo wordmark, headers, links, buttons, column headers, accent bars, chart primary series |
| Apex Blue Deep | `--apex-blue-deep` | `#1D225E` | 29, 34, 94 | Large dark areas. Header bands, hero grounds, full-width strips, section dividers, footers, table header rows |
| Apex Blue Light | `--apex-blue-light` | `#9699C7` | 150, 153, 199 | Tertiary accents, hover states, lighter highlights |
| Apex Gold | `--apex-gold` | `#FDB61C` | 253, 182, 28 | Signature accent, echoing the arc. Band rules, kicker marks, highlight underlines, stat numerals on dark |
| Apex Gold Deep | `--apex-gold-deep` | `#B77808` | 183, 120, 8 | Gold text on white at 3.68:1. 18pt print or 24px web and up, the `.bk-h3` step and above, and icons. Never small text |
| Black | `--apex-black` | `#000000` | 0, 0, 0 | High-contrast headings on light grounds |
| White | `--apex-white` | `#FFFFFF` | 255, 255, 255 | Text on dark grounds, page background |

### Neutrals

| Name | Variable | Hex | RGB | Usage |
|---|---|---|---|---|
| Charcoal | `--apex-charcoal` | `#1E293B` | 30, 41, 59 | Primary body text on light |
| Muted | `--apex-muted` | `#64748B` | 100, 116, 139 | Secondary text, metadata, footer text |
| Dimmed | `--fg-4` | `#94A3B8` | 148, 163, 184 | Dimmed labels only. Never body text |
| Hairline | `--apex-hairline` | `#E2E8F0` | 226, 232, 240 | Table borders, rules, footer top border |
| Border 2 | `--border-2` | `#CBD5E1` | 203, 213, 225 | Heavier dividers, input borders |
| Surface Tint | `--apex-surface` | `#f3f3fb` | 243, 243, 251 | Alternating rows, callout fills, subtle panels |

### Semantic layer

Style through these. The names are identical in every brand kit, so a component written for Apex renders correctly for Royal with only `palette.css` swapped.

| Variable | Resolves to | Use |
|---|---|---|
| `--fg-1` | `#1E293B` | Primary text on light |
| `--fg-2` | `#64748B` | Secondary text |
| `--fg-3` | `#64748B` | Tertiary, metadata, eyebrows |
| `--fg-4` | `#94A3B8` | Dimmed labels |
| `--fg-accent` | `#2B338D` | Brand-colored text |
| `--fg-on-dark-1` | `#FFFFFF` | Primary text on dark |
| `--fg-on-dark-2` | `#D6DAEC` | Body text on dark |
| `--fg-on-dark-3` | `#9EA5C4` | Captions and eyebrows on dark |
| `--bg-canvas` | `#FFFFFF` | Page ground |
| `--bg-surface` | `#f3f3fb` | Panels, alternating rows |
| `--bg-elevated` | `#FFFFFF` | Cards |
| `--bg-inverse` | `#1D225E` | Inverted panels |
| `--bg-band` | `#1D225E` | Header band |
| `--border-1` | `#E2E8F0` | Hairline |
| `--border-2` | `#CBD5E1` | Heavier divider |
| `--border-on-dark` | `rgba(255,255,255,0.12)` | Dividers on dark |
| `--border-band-rule` | `#FDB61C` | The 3px gold rule under the header band |

### Status

Identical in every brand, so an operational signal never changes meaning between documents. A brand accent is never a status color.

| Role | Variable | Hex | On `#FFFFFF` | As text |
|---|---|---|---|---|
| Go | `--status-go` | `#1E7A4D` | 5.32:1 | Any size |
| Warn | `--status-warn` | `#B5821A` | 3.40:1 | 18pt or 24px and up. Never running copy |
| Stop | `--status-stop` | `#B0322B` | 6.29:1 | Any size |
| Info | `--status-info` | `#2A5A8C` | 7.14:1 | Any size |

### Diagram roles

Identical in every brand, so a flowchart reads the same regardless of whose document it sits in. Never invent a new hue for these roles.

| Role | Fill | Border | Use |
|---|---|---|---|
| Decision | `#4a8e3a` | `#3a7029` | Decision boxes, questions, branch points |
| Warning | `#f57c00` | `#cc6600` | Warnings, advisories, watch-out pills |
| Process | `#3e3e3e` | `#2a2a2a` | Neutral process steps, context boxes |
| Connector | `#3e3e3e` stroke | 1.8pt | Lines between nodes, with arrow markers |

All diagram shapes are rectangles at 6px radius. Role is communicated by fill, never by shape.

White node text on `#f57c00` measures 2.70:1 and on `#4a8e3a` measures 4.02:1. Both fail 4.5:1. The two fills and their white text are inherited from the pre-v1.0 kits and are frozen pending a decision from the brand owner. Do not recolor them. Until that decision lands, a Decision or Warning node carries a short label only, and every fact it signals also appears in the running text or the table beside the diagram.

---

## 2. Color rules

### What each color must never do

| Color | Never |
|---|---|
| Apex Gold `#FDB61C` | Never text on white. Never a background for a large area. Never a status color. Never the fill of a body-text panel |
| Apex Gold Deep `#B77808` | Never below 18pt print or 24px web, the `.bk-h3` step. Never an eyebrow, a caption or a table cell. Never long-form running text |
| Apex Blue Light `#9699C7` | Never text on white. Never a large-area background. Never a table header fill |
| Apex Blue `#2B338D` | Never a body-text color for long-form. Never carries `--fg-on-dark-3` `#9EA5C4`, which measures 4.40:1 on it |
| Surface Tint `#f3f3fb` | Never carries white text. Never a header band |
| Dimmed `#94A3B8` | Never body text on white |
| Muted `#64748B` | Never text on `#1D225E` |

### Contrast traps

1. **Bright gold on white.** `#FDB61C` on `#FFFFFF` measures 1.77:1. `#B77808` measures 3.68:1, which clears the 3:1 large-text threshold and nothing below it. Gold text on white runs at 18pt print or 24px web and up, which is the `.bk-h3` step and above. Body copy, `.bk-body-sm`, `.bk-caption` and `.bk-eyebrow` are `--fg-1`, `--fg-2` or `--fg-accent`, never gold.
2. **Gold as a status signal.** Gold reads as the Apex accent, so a gold warning pill is indistinguishable from a brand highlight. `--status-warn` `#B5821A` measures 3.40:1 on white, so it marks a warning as a rule, a chip border or a label at 18pt or 24px and up. The warning sentence itself is `--fg-1`. Inside a flowchart node the warning fill is `#f57c00`, which is frozen and fails as a ground for text.
3. **Blue Light as text.** `#9699C7` on white measures 2.74:1. It is an accent hue, not an ink. Confine it to hover states, thin rules and tertiary marks.
4. **Muted on the band.** `#64748B` on `#1D225E` is nearly invisible. Text on the band uses `--fg-on-dark-1`, `--fg-on-dark-2` or `--fg-on-dark-3`.
5. **Gold over blue.** `#FDB61C` on `#1D225E` measures 8.24:1 and on `#2B338D` measures 6.06:1. Both clear 4.5:1 at any size, so gold on either blue is correct for a stat numeral, an accent rule or a caps label on a dark band.
6. **Secondary grey as the data.** `#64748B` measures 4.76:1 on `#FFFFFF` but 4.31:1 on the `#f3f3fb` alternating row, which fails. `.bk-body-sm` and `.bk-caption` default to that grey, so any table cell carrying primary data sets `color: var(--fg-1)` `#1E293B`, which measures 13.25:1 on `#f3f3fb`.

### Measured contrast

Computed against WCAG 2.x relative luminance. Use these figures. Do not restate a different one.

| Pair | Ratio | Verdict |
|---|---|---|
| `#1E293B` on `#FFFFFF` | 14.63:1 | Any size |
| `#2B338D` on `#FFFFFF` | 10.71:1 | Any size |
| `#1E293B` on `#f3f3fb` | 13.25:1 | Any size |
| `#64748B` on `#FFFFFF` | 4.76:1 | Any size |
| `#64748B` on `#f3f3fb` | 4.31:1 | Fails. Never on the alternating row |
| `#B77808` on `#FFFFFF` | 3.68:1 | Large or bold only. Never small text |
| `#B5821A` on `#FFFFFF` | 3.40:1 | Large or bold only. Never running copy |
| `#9699C7` on `#FFFFFF` | 2.74:1 | Fails. Never text |
| `#FDB61C` on `#FFFFFF` | 1.77:1 | Fails. Never text |
| `#FDB61C` on `#1D225E` | 8.24:1 | Any size |
| `#FDB61C` on `#2B338D` | 6.06:1 | Any size |
| `#FFFFFF` on `#1D225E` | 14.56:1 | Any size |
| `#FFFFFF` on `#2B338D` | 10.71:1 | Any size |
| `#9EA5C4` on `#2B338D` | 4.40:1 | Fails 4.5:1. Never a caption or an eyebrow on this ground |
| `#FFFFFF` on `#3e3e3e` | 10.70:1 | Any size |
| `#FFFFFF` on `#4a8e3a` | 4.02:1 | Fails 4.5:1. Frozen diagram fill |
| `#FFFFFF` on `#f57c00` | 2.70:1 | Fails. Frozen diagram fill |

Large text starts at 18pt or 24px regular, 14pt or 18.66px bold. The `.bk-h4` step is 15pt at weight 600, which is neither, so the weight-independent floor for a 3:1 color is the `.bk-h3` step: 18pt print, 24px web. The body step is 12pt print and 16px web, which is normal text and needs 4.5:1.

### Backgrounds

White is the primary ground. The only other permitted subtle ground is `#f3f3fb`. Never anything stronger for an alternating row, a callout or a panel. Dark grounds are `#1D225E` only.

### Data and functional color

Chart series and status indicators stay within the blue and gold palette or harmonize with it. Where a chart needs more series than the palette provides, extend along the blue ramp rather than introducing a new hue. Decorative off-brand color is never permitted.

---

## 3. Logo

### Lockups

| Lockup | What it is | When |
|---|---|---|
| Horizontal | The blue `APEX PARAMEDICS` wordmark under the gold arc | The main logo. Default for any context with horizontal room |
| Compact | `APEX` alone under the gold arc | Smaller places, decks, or a corner |
| Mark | The gold arc alone | Favicons, badges, social avatars, table corners |

Apex has no stacked lockup. Where a vertical lockup is needed, use the horizontal one at reduced width.

### Specifications

| Property | Value |
|---|---|
| Horizontal viewBox | `0 0 687.72 289.25` |
| Horizontal aspect | 2.378 : 1 |
| Compact viewBox | `0 0 682.3 240.66` |
| Compact aspect | 2.835 : 1 |
| Mark viewBox | `-8 -8 619 245` |
| Wordmark color | Apex Blue `#2B338D`, or `#FFFFFF` on dark |
| Arc color | Apex Gold `#FDB61C`, on both light and dark |
| Minimum clear space | Padding on all four sides equal to at least the height of the gold arc |
| Minimum size, horizontal | 110px on screen, 1 inch in print |
| Minimum size, compact | 80px on screen, 0.75 inch in print |
| Minimum size, mark | 32px |
| Vector master | `assets/logos/source/apex-paramedics-PMS123-PMS072.eps` |

The shipping SVGs are converted from the EPS, which remains the authoritative master for any future re-export.

The horizontal files are tight to their ink. The superseded `0 0 894.53333 430.01334` box carried 12.5 percent empty height below the mark, so at the same pinned width the logo renders at the same size and the box around it is shorter. Rendered at 800px wide the box is 384.57px tall in the old file and 336.47px in the new one, and the ink is 336.47px tall in both. No pinned width in this kit changes.

The compact minimum holds the `APEX` cap at or above the size the horizontal lockup shows at its own 110px floor. Rendered at 1000px wide the cap measures 165.50px in the horizontal file and 230.14px in the compact file, so 110px horizontal matches 79.10px compact.

The delivered compact files carried `#000F9F` and `#FFB71B`. Both fills are normalised to the primary lockup, `#2B338D` and `#FDB61C`, so the house ships one blue and one gold. The delivered originals are in the git history, at the commit that adopted the set.

### Raster fallback

The `-on-dark` SVG is the correct file for the `#1D225E` band. Where only the color raster exists and no SVG is reachable, place that raster on a white chip inside the band rather than knocking the logo out or filtering it: `#FFFFFF` fill, `--radius-sm` 2px, clear space held on all four sides. A white chip is also the fix for a busy photographic ground.

### Do not

- Do not stretch, skew or rotate the logo.
- Do not place the logo on a busy photographic background without a solid backing chip.
- Do not recolor the logo to anything other than Apex Blue plus Apex Gold, or white plus gold on dark.
- Do not apply a CSS filter to invert or recolor a variant. Load the correct file for the ground.
- Do not add a drop shadow, glow, outline or gradient.
- Do not separate the wordmark from the arc in the horizontal lockup.
- Do not use the compact lockup where the horizontal one fits. `APEX PARAMEDICS` is the main logo.
- Do not render the arc in blue or the wordmark in gold.
- Do not reproduce the logo below its minimum size.
- Do not crop the clear space to fit a tight layout. Shrink the logo instead, down to the minimum.

### Embedding

Reference the CDN URL directly with `<img src="...">`. The repository is public and jsDelivr needs no auth. Do not inline a copied SVG path, because it will drift from the master.

---

## 4. Voice and content

Apex speaks the way a field crew speaks: short, specific, and about the work.

- Period sentences, active verbs. No throat-clearing, no hedging, no filler.
- Never an em dash. Use a period, a comma, or a middot separator.
- A label, a value, and nothing between them. No helper text under a field, no caption restating the number above it, no parenthetical after a heading.
- Exact values only. Write `#1D225E`, never “the dark navy”. Write the real number, never a rounded one.
- Clinical and operational terms stay precise. Never soften a protocol term for readability.
- Any string a person retypes, dictates or reads aloud goes in the mono face: unit IDs, run numbers, authorization numbers, MRNs. Use `.bk-code`.
- Write a caption only when it carries information the thing above it does not.
- No off-brand decoration. If information can be carried by structure, position or a rendered example, carry it that way.

---

## 5. Legacy asset URLs

Still served, still valid, retained for anything already pointing at them.

| Asset | URL |
|---|---|
| Brand colors, raw JSON | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/colors.json` |
| Legacy base CSS | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/brand-base.css` |
| Montserrat, this kit’s copy | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf` |

New work loads `type-system.css` plus `palette.css` and reads colors from `tokens.json`. The house font is served from the Collective Edge kit so there is one font file and one place to update it.
