# Apex Paramedics brand kit

House type system v1.0. Cloud-hosted brand assets, a Claude skill, and print-ready templates for Apex Paramedics.

Apex Paramedics is an operating company under Collective Edge. Across the house exactly two things vary between brands: palette and logo. Type is shared and identical, and it is what makes Apex, Royal and Collective Edge read as one house. Never fork the type layer.

Everything is served from jsDelivr, so any session on any machine can produce on-brand material with no local setup.

## What is in here

```
apex-brand-kit/
├── SKILL.md                        The skill an agent loads. Brand identity, then pointers.
├── brands.json                     Registry of every brand in the house. Shared, identical everywhere.
├── tokens.json                     Apex colors, machine-readable, for generators that cannot parse CSS.
├── NEW-BRAND.md                    How to add a brand. Shared, identical everywhere.
├── reference/
│   ├── brand.md                    Palette, measured contrast, logo rules, voice.
│   ├── layout.md                   Header band, sub-banner, flowchart, stats, tables, footer.
│   └── type-system.md              The type standard. Shared, identical everywhere.
├── snippets/
│   ├── type-system.css             The type layer. Shared, identical everywhere.
│   ├── palette.css                 The only stylesheet that differs between brands.
│   ├── type-tokens.json            Type values for non-CSS generators. Shared.
│   ├── header-band.html            Drop-in header band.
│   └── brand-base.css              DEPRECATED shim. Kept for live pages. Replaced by the two above.
├── templates/
│   ├── document.html               Letter one-pager and report letterhead, print-ready.
│   └── deck.html                   Five slides at 16:9, one landscape page each.
├── Examples/
│   ├── apex-one-pager.html         Shipping specimen.
│   └── apex-one-pager.before.html  The same page before v1.0, for comparison.
├── scripts/
│   ├── validate.py                 Mechanical check of rules 1, 2, 5, 9, 10, 13 and 14. Shared.
│   └── check-sync.py               Asserts the seven shared files have not drifted. Shared.
└── assets/
    ├── colors.json                 DEPRECATED. Replaced by tokens.json.
    ├── fonts/Montserrat-VariableFont_wght.ttf
    └── logos/                      horizontal and mark, color and white, plus the source EPS.
```

Seven files are byte-identical in every kit: `reference/type-system.md`, `NEW-BRAND.md`, `brands.json`, `snippets/type-system.css`, `snippets/type-tokens.json`, `scripts/validate.py`, `scripts/check-sync.py`. `check-sync.py` fails if any of them drifts.

## Loading the brand in HTML

Two stylesheets, in this order. The type layer is served from the parent brand because type belongs to Collective Edge.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/snippets/type-system.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/palette.css">
```

Style through the `.bk-*` classes and the semantic `--fg-*` / `--bg-*` / `--border-*` variables. Reach for a raw `--apex-*` value only where the brand color is the point: a logo band, an accent rule, a chart series.

For a PDF pipeline (weasyprint, wkhtmltopdf, Chrome print) embed the font. `templates/document.html` carries the block:

```css
@font-face {
  font-family: 'Montserrat';
  src: url('https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/assets/fonts/Montserrat-VariableFont_wght.ttf') format('truetype');
  font-weight: 400 800;
  font-style: normal;
}
```

`400 800` is the permitted range. `reference/type-system.md` section 3 bans 100, 200, 300 and 900 at document sizes.

## Logo roles

Ask for a role, never a filename. `-on-light` is the file you place on a light background.

| Role | File |
|---|---|
| `horizontal-on-light` | `assets/logos/horizontal-color.svg` |
| `horizontal-on-dark` | `assets/logos/horizontal-white.svg` |
| `mark-on-light` | `assets/logos/mark-color.svg` |
| `mark-on-dark` | `assets/logos/mark-white.svg` |
| `stacked-on-dark` | Apex has none. Use `horizontal-on-dark`. |

Reference the CDN URL directly with `<img src="...">`. The repository is public and jsDelivr needs no auth. `assets/logos/source/apex-paramedics.eps` is the authoritative master for any re-export.

## Color

| Name | Variable | Hex | Usage |
|---|---|---|---|
| Apex Blue | `--apex-blue` | `#2c338e` | Headers, links, buttons, accent bars, chart primary |
| Apex Blue Deep | `--apex-blue-deep` | `#1D225E` | Header bands, hero grounds, footers, table header rows |
| Apex Blue Light | `--apex-blue-light` | `#9699C7` | Tertiary accents and hover. 2.74:1 on white, never text |
| Apex Gold | `--apex-gold` | `#f9ad16` | Band rules, accent marks, stat numerals on dark. 1.91:1 on white, never text |
| Apex Gold Deep | `--apex-gold-deep` | `#B77808` | Gold text on white at 3.68:1. 18pt print or 24px web and up, the `.bk-h3` step and above |
| Surface Tint | `--apex-surface` | `#f3f3fb` | Alternating rows, callout fills |

Blue is the structure. Gold is the spark. Pantone Blue 072 C is the wordmark, Pantone 1235 C is the arc.

The full measured contrast table, including the frozen diagram fills, is in `reference/brand.md`.

## Installing the skill

```bash
git clone https://github.com/collective-edge/apex-brand-kit ~/.claude/skills/apex-brand-guidelines
```

Claude reads `SKILL.md` and applies the brand. To update:

```bash
cd ~/.claude/skills/apex-brand-guidelines && git pull
```

## Before shipping anything

```bash
python3 scripts/validate.py path/to/output.html
python3 scripts/check-sync.py
```

`validate.py` exits non-zero on a violation of rules 1, 2, 5, 9, 10, 13 or 14. It cannot see pixels, so render the file and look at it as well. The rest of the checklist is in `SKILL.md`.

## Versioning

`@main` serves the latest. Pin to a tag for stability: replace `@main` with `@v1.0`. Bump the tag on a breaking brand change: a logo redesign or a color shift. The type system versions separately, per `reference/type-system.md` section 13.

## License

Brand assets are property of Apex Paramedics. Use only for Apex Paramedics and partner-related material.
