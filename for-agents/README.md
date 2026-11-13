# Apex Paramedics · for agents

You are producing something for Apex Paramedics. This page is the shortest correct path. [`SKILL.md`](../SKILL.md) is the full standard, and it wins any disagreement with this page.

Apex Paramedics is an operating company under Collective Edge. Blue and gold palette, the arc wordmark, the house type system.

Working for a person instead? Send them to [`for-humans/`](../for-humans/).

## 1. Load the brand

Every file is public on jsDelivr. No auth, no install.

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/
```

HTML takes these stylesheets, in this order:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/snippets/type-system.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/palette.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/snippets/data-color.css">
```

`type-system.css` and `data-color.css` are served from the Collective Edge kit for every brand. `palette.css` is the only file that differs. Load `data-color.css` only when the page has a chart, a dashboard tile or a reported number.

For print or PDF, add the face inline and select it:

```css
@font-face {
  font-family: "Montserrat";
  src: url("https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.woff2") format("woff2-variations"),
       url("https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf") format("truetype-variations");
  font-weight: 400 800;
  font-style: normal;
}
html, body { font-family: "Montserrat", "Helvetica Neue", Helvetica, Arial, sans-serif; }
```

Style through the `.bk-*` classes and the `--fg-*`, `--bg-*` and `--border-*` variables. Those names are identical in all three brands. Start from [`templates/`](../templates/) and [`snippets/header-band.html`](../snippets/header-band.html) instead of a blank page.

## 2. Get a logo by role

Ask for a role, never a filename. Filenames differ between brands. `-on-light` is the file you place on a light background.

| Role | URL | Place on |
|---|---|---|
| `horizontal-on-light` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-color.svg` | A light background |
| `horizontal-on-dark` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg` | A dark background |
| `compact-on-light` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/compact-on-light.svg` | A light background |
| `compact-on-dark` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/compact-on-dark.svg` | A dark background |
| `mark-on-light` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/mark-color.svg` | A light background |
| `mark-on-dark` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/mark-white.svg` | A dark background |

`stacked-on-dark` does not exist for this brand. Use `horizontal-on-dark`.

Embed with `<img src="...">`. Do not inline a copied SVG path, because it drifts from the master.

Transparent PNG, for generators that cannot place SVG:

| Role | URL |
|---|---|
| `horizontal-on-light` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/for-humans/logos/png/Apex-Paramedics-horizontal-blue-1200w.png` |
| `horizontal-on-dark` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/for-humans/logos/png/Apex-Paramedics-horizontal-white-1200w.png` |
| `compact-on-light` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/for-humans/logos/png/Apex-Paramedics-compact-blue-1200w.png` |
| `compact-on-dark` | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/for-humans/logos/png/Apex-Paramedics-compact-white-1200w.png` |

Each PNG also ships at double width. Replace the width in the filename: `1200w` to `2400w`, `512w` to `1024w`.

## 3. Color

| Name | Variable | Hex | Use |
|---|---|---|---|
| Apex Blue | `--apex-blue` | `#2B338D` | Headers, links, buttons, accent bars |
| Apex Blue Deep | `--apex-blue-deep` | `#1D225E` | Header bands, hero grounds, footers, table header rows |
| Apex Blue Light | `--apex-blue-light` | `#9699C7` | Tertiary accents and hover only |
| Apex Gold | `--apex-gold` | `#FDB61C` | Band rules, accent marks, stat numerals on dark |
| Apex Gold Deep | `--apex-gold-deep` | `#B77808` | Gold text on white, large only |
| Charcoal | `--apex-charcoal` | `#1E293B` | Body text on light |
| Surface Tint | `--apex-surface` | `#f3f3fb` | Alternating rows, callout fills |

Every value, including the semantic, status and on-dark sets, as JSON:

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/tokens.json
```

## 4. The rules that get broken

1. Apex Gold `#FDB61C` is never text on white. It measures 1.77:1. On `#1D225E` it measures 8.24:1 and is correct.
2. Gold text on white is `#B77808`, at 18pt print or 24px web and up. Never a caption, a table cell or body copy.
3. Apex Blue Light `#9699C7` is never text. It measures 2.74:1 on white.
4. Gold is a brand accent, never a status color. Warnings use `--status-warn`.
5. Use the horizontal lockup wherever it fits. Compact is for where it does not.
6. Chart and dashboard color comes from `data-color.css`, in series order. A brand color is never a chart series.
7. Match the logo file to the background. Never recolor or invert a logo with CSS.
8. Montserrat only, weights 400 to 800. No italic, at any weight.
9. No em dashes in copy. A period, a comma, or `·`.
10. For print or PDF, inline the `@font-face` block. A locally installed font renders right on one machine and wrong everywhere else.

## 5. Not writing HTML

| Output | Read |
|---|---|
| python-pptx, python-docx, matplotlib, reportlab | `tokens.json` for color, [`snippets/type-tokens.json`](../snippets/type-tokens.json) for sizes, weights and tracking |
| A font file to embed | [`for-humans/fonts/static/`](../for-humans/fonts/static/) · Regular 400, SemiBold 600, Bold 700, ExtraBold 800 |
| A raster logo | The PNG table above |
| A chart | [`reference/data-color.md`](../reference/data-color.md). The hex values are in `snippets/data-color.css` |

This kit ships no photography. Do not generate or source a stand-in without being asked.

## 6. Read next, by task

| Making | Read |
|---|---|
| Anything | [`SKILL.md`](../SKILL.md), start to finish. It ends with the pre-ship check |
| A header band, table, stat callout, flowchart, footer | [`reference/layout.md`](../reference/layout.md) |
| A chart, dashboard or scorecard | [`reference/data-color.md`](../reference/data-color.md) |
| Buttons, inputs, product UI | [`reference/ui.md`](../reference/ui.md) |
| Long-form type decisions | [`reference/type-system.md`](../reference/type-system.md) |
| A contrast or logo question | [`reference/brand.md`](../reference/brand.md) |

## 7. Verify before you report done

```bash
python3 scripts/validate.py path/to/output.html
python3 scripts/ui-audit.py path/to/output.html
python3 scripts/validate-palette.py --series
```

`validate.py` exits non-zero on a mechanical rule violation. None of the scripts can see overlap, clipping or a fallback font. Render the file and look at it. If you cannot render, say so instead of reporting it clean.

## 8. Install as a skill

Clone the kit into the skills directory your agent reads. The path differs by tool.

```bash
git clone https://github.com/collective-edge/apex-brand-kit ~/skills/apex-brand-guidelines
```

`SKILL.md` at the root carries the frontmatter. `git pull` updates it.

## 9. The other brands

One registry resolves every brand in the house to its CDN root, palette, tokens and logo roles. It is identical in all three kits.

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/brands.json
```

| Brand | Kit | Entry point |
|---|---|---|
| Royal Ambulance | [`royal-brand-kit`](https://github.com/collective-edge/royal-brand-kit) | [for agents](https://github.com/collective-edge/royal-brand-kit/tree/main/for-agents) |
| Collective Edge | [`collective-edge-brand-kit`](https://github.com/collective-edge/collective-edge-brand-kit) | [for agents](https://github.com/collective-edge/collective-edge-brand-kit/tree/main/for-agents) |
