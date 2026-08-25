---
name: apex-brand-guidelines
description: Applies Apex Paramedics brand standards, the navy-and-gold palette, the shared house type system, the seven logo roles, and the Apex house layout patterns, to any output that represents Apex Paramedics. Use when generating or reviewing an Apex Paramedics email, slide, deck, one-pager, report, letterhead, flyer, proposal, document, web page, table, chart, diagram, or PDF. Also covers Apex social posts, internal comms, and training materials, and any artifact carrying the Apex logo or colors. Provides CDN asset loading, the color rules agents get wrong most often, a pointer to the house type standard, copy-pasteable layout blocks, and the pre-ship validator command.
---

# Apex Paramedics

Apex Paramedics is an operating company under Collective Edge. It runs a navy-blue and gold palette drawn from its own mark.

Across the house, exactly two things vary between brands: palette and logo. Type is shared and identical. Never fork the type layer.

---

## 1. Asset loading

Everything is cloud-hosted on jsDelivr. Never look for local files.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/snippets/type-system.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/palette.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/snippets/cobrand.css">
```

Load them in that order. `cobrand.css` is the co-brand lockup, shared and identical in every kit, and it reads the palette, so it loads last. `type-system.css` is identical in every kit and is served from the parent brand. `palette.css` is the only stylesheet that differs.

For PDF pipelines (weasyprint, wkhtmltopdf, Chrome print), embed the font:

```css
@font-face {
  font-family: 'Montserrat';
  src: url('https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf') format('truetype');
  font-weight: 400 800;
  font-style: normal;
}
body { font-family: 'Montserrat', Calibri, Arial, sans-serif; }
```

### Logo roles

Ask for a role, never a filename. `-on-light` is the file you place **on** a light background.

| Role | File | URL |
|---|---|---|
| `horizontal-on-light` | `horizontal-color.svg` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-color.svg` |
| `horizontal-on-dark` | `horizontal-white.svg` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg` |
| `compact-on-light` | `compact-on-light.svg` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/compact-on-light.svg` |
| `compact-on-dark` | `compact-on-dark.svg` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/compact-on-dark.svg` |
| `mark-on-light` | `mark-color.svg` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/mark-color.svg` |
| `mark-on-dark` | `mark-white.svg` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/mark-white.svg` |
| `stacked-on-dark` | none | Apex has no stacked lockup. Use `horizontal-on-dark`. |

The horizontal lockup is the main logo, `APEX PARAMEDICS`. The compact lockup is `APEX` alone, for smaller places, decks, or a corner.

Reference a logo with `<img src="...">`. The CDN is public, no auth.

Machine-readable colors for python-pptx, python-docx, matplotlib and reportlab: [`tokens.json`](tokens.json). Type values for those generators: [`snippets/type-tokens.json`](snippets/type-tokens.json).

Every brand in the house, with its CDN root, palette, logo roles and Collective Edge co-brand marks, resolves from [`brands.json`](brands.json). Look a sibling brand up there, never by guessing a filename. Adding a brand: [`NEW-BRAND.md`](NEW-BRAND.md).

---

## 2. Color

| Name | Variable | Hex | Usage |
|---|---|---|---|
| Apex Blue | `--apex-blue` | `#2B338D` | Headers, links, buttons, accent bars, chart primary |
| Apex Blue Deep | `--apex-blue-deep` | `#1D225E` | Header bands, hero grounds, footers, table header rows |
| Apex Blue Light | `--apex-blue-light` | `#9699C7` | Tertiary accents, hover states |
| Apex Gold | `--apex-gold` | `#FDB61C` | Band rules, kicker marks, stat numerals on dark |
| Apex Gold Deep | `--apex-gold-deep` | `#B77808` | Gold text on white. 3.68:1, so 18pt print or 24px web and up. `.bk-h3` and above |
| Surface Tint | `--apex-surface` | `#f3f3fb` | Alternating rows, callout fills |

Style through the semantic layer (`--fg-*`, `--bg-*`, `--border-*`). Reach for a raw `--apex-*` value only where the brand color is the point: a logo band, an accent rule, a chart series.

Three traps agents fall into:

1. **Bright gold `#FDB61C` is never text on white.** It measures 1.77:1. `#B77808` measures 3.68:1, which clears the 3:1 large-text threshold and nothing else, so it runs at 18pt print or 24px web and up, the `.bk-h3` step and above. Never an eyebrow, a caption, a table cell or body copy. Body text is `--fg-1`.
2. **Gold is never a large-area background** and never a status color. It vibrates at scale. `--status-warn` `#B5821A` measures 3.40:1 on white, so it carries a rule, a chip border or a label at 18pt or 24px and up. The warning sentence itself is `--fg-1`.
3. **Apex Blue Light `#9699C7` is never text on white.** It measures 2.74:1. Tertiary accents, thin rules and hover states only, never a background.

Full palette with RGB, every contrast rule, and what each color must never do: [`reference/brand.md`](reference/brand.md).

---

## 3. Type

Type is shared house property. Do not restate it, do not adapt it, do not fork it.

**Read [`reference/type-system.md`](reference/type-system.md) before setting any type.** It carries the measured metrics, the weight ladder, the scale table in px and pt, measure, composition, micro-typography, and the fifteen rules.

Three things that are never negotiable:

1. **No italic.** Any weight, any size, any medium. Never synthesize an oblique.
2. **No weight outside 400, 600, 700, 800.** 400 body, 600 subheads and caps labels, 700 headings and stat numerals, 800 hero display only.
3. **No px tracking.** Letter-spacing is always em. A px value is a different optical amount at every size.

On any dark ground, put `.bk-on-dark` on the container. The CSS adds 0.005em tracking at every step, and drops one weight where the step is 700 or heavier. 600 is the floor.

---

## 4. Layout

Blue is the structure. Gold is the spark.

Header band, sub-banner, flowchart nodes, stat callouts, tables and footer, each as a copy-pasteable block: [`reference/layout.md`](reference/layout.md).

The header band, which opens nearly every Apex deliverable:

```html
<header class="bk-on-dark" style="background:var(--bg-band); border-bottom:3px solid var(--border-band-rule);
        padding:0.32in 0.5in; display:flex; align-items:center; justify-content:space-between; gap:24px;">
  <div class="bk-display-md bk-caps" style="max-width:none; margin:0;">Field operations brief</div>
  <img src="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg"
       alt="Apex Paramedics" style="width:1.6in; height:auto; display:block; flex:0 0 auto;">
</header>
```

`.bk-on-dark` resolves `.bk-display-md` to weight 700 and tracking 0.030em. `--border-band-rule` is the 3px gold rule. Same file lives at [`snippets/header-band.html`](snippets/header-band.html).

**Powered by Collective Edge.** Apex is an operating company under Collective Edge, and the reader should be able to see it. The lockup rides beside the Apex mark, never inside it, with a hairline between them, at 204px, which is wider than the Apex mark above it on purpose. `.ce-powered` on a dark band, `.ce-powered ce-powered-light` on white, `.ce-powered-text` where no mark fits. It belongs on footers, dashboard sidebars, closing slides, data pages, anywhere a number was computed rather than typed. Never on the Apex mark itself, never on a clinical instruction or a patient-facing consent, never twice on one surface. Both grounds, the measured contrast and copy-pasteable blocks: [`reference/layout.md`](reference/layout.md) section 7.

`.bk-caps` works at every step. Each step declares its own `--tr-caps` and one rule applies it, so `.bk-h1.bk-caps` opens to +0.030em and `.bk-body.bk-caps` to +0.070em. Rule 7 puts uppercase on a title, band or divider surface and on labels, and sentence case on headings inside a document. A band title is a title surface, so it takes `bk-caps`. For a one-pager, swap `.bk-display-md` for `.bk-h1` and keep `bk-caps`, which resolves on dark to 30pt, weight 600, tracking 0.035em.

---

## 5. Verify before shipping

```bash
python3 scripts/validate.py path/to/output.html
```

It checks rules 1, 2, 5, 9, 10, 13 and 14 mechanically and exits non-zero on a violation. It cannot see pixels. Confirm the rest by eye:

- [ ] Rendered and looked at, not just written. Overlap, clipping and overflow are invisible in source. If your environment cannot render, say so plainly instead of claiming it looks clean.
- [ ] Montserrat actually rendered, not a fallback. For PDF, actually embedded in the file.
- [ ] No italic anywhere.
- [ ] Correct logo role for the ground. White variant on `#1D225E`, never a CSS filter.
- [ ] Clear space held. Horizontal logo at least 110px wide, compact at least 80px, mark at least 32px.
- [ ] “Powered by Collective Edge” on the footer, the sidebar or the closing slide. Once, beside the Apex mark and never inside it.
- [ ] Bright gold `#FDB61C` nowhere near body text on white.
- [ ] Dark bands one weight lighter than their light-surface equivalent, down to the 600 floor.
- [ ] Body text not running the full container width.
- [ ] Every color drawn from the palette. No off-brand hues.
- [ ] Page breaks clean, tables not split across pages.

Name the brand choices you applied when you hand the work back: which logo role, which accent, how the font embedded.

---

## 6. Versioning

`@main` serves the latest. Pin to a tag for stability: replace `@main` with `@v1.1`. Bump the tag on a breaking brand change: a logo redesign or a color shift.
