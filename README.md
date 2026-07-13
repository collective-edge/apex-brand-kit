# Apex Paramedics Brand Kit

Cloud-hosted brand assets and Claude skill for Apex Paramedics — a navy-blue + gold color palette, Montserrat typography, the horizontal wordmark + arc mark, plus a `SKILL.md` that teaches Claude to apply the brand consistently to any document, slide, flowchart, or one-pager.

Anyone with this repo URL or the CDN links below can produce on-brand Apex materials from any machine, with no local setup beyond a working Claude session. Montserrat is shared across every Collective Edge operating company (Apex, Royal, CE) — only the **colors and logo** distinguish the brands.

## What's in here

```
apex-brand-kit/
├── SKILL.md                 # The brand skill Claude reads
├── assets/
│   ├── colors.json          # Source of truth for hex codes
│   ├── fonts/
│   │   └── Montserrat-VariableFont_wght.ttf
│   └── logos/
│       ├── horizontal-color.svg    # primary lockup (navy wordmark + gold arc)
│       ├── horizontal-white.svg    # dark-background variant (white wordmark + gold arc)
│       ├── mark-color.svg          # arc-only mark
│       ├── mark-white.svg          # arc-only mark, white
│       ├── horizontal-color.png    # raster fallback
│       └── source/
│           └── apex-paramedics.eps # authoritative vector source
├── snippets/
│   ├── brand-base.css       # Drop-in CSS with @font-face + variables
│   └── header-band.html     # Drop-in header markup
└── Examples/                # Working examples using only CDN URLs
```

The SVG logos are traced from the Apex artwork; `assets/logos/source/apex-paramedics.eps` remains the authoritative source for any future re-export.

## CDN base URL

All assets are served via [jsDelivr](https://www.jsdelivr.com/) from the `main` branch — fast, free, and globally cached:

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/
```

Append the path inside this repo to fetch any file. Example for the horizontal logo:

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-color.svg
```

## Quick start — using the brand in any HTML

Add this to the top of any HTML document and you have Montserrat plus all the brand color variables:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/brand-base.css">
```

For embedding Montserrat into a printed PDF (weasyprint, wkhtmltopdf, Chrome print-to-PDF), include the `@font-face` declaration inline so the font travels with the file. See `SKILL.md` for the snippet.

## Quick start — installing the Claude skill

So Claude automatically applies the brand whenever you ask for Apex materials, install the skill into your local Claude skills folder:

```bash
git clone https://github.com/collective-edge/apex-brand-kit ~/.claude/skills/apex-brand-guidelines
```

That's it. Claude will pick up `SKILL.md` and apply the brand standards automatically. To update, run:

```bash
cd ~/.claude/skills/apex-brand-guidelines && git pull
```

## Sharing with teammates

Send them this repo URL or paste the install command above. The CDN means generated documents (HTML, PDFs with embedded fonts) work for recipients who don't have the skill installed — the assets are fetched at render time.

## Color reference

See `assets/colors.json` for the machine-readable source of truth, or `SKILL.md` for human-readable usage rules.

| Name | Hex | Use |
|---|---|---|
| Apex Blue | `#134891` | Primary — wordmark, headers, links, buttons |
| Apex Blue Deep | `#0E3468` | Hero headers, full-width bands, footers |
| Apex Blue Light | `#95ADCE` | Tertiary accents only |
| Apex Gold | `#FFC92B` | Signature accent — the arc, kickers, highlights |
| Apex Gold Deep | `#B98900` | Text-safe gold for labels on white |
| Surface | `#f2f6fc` | Very light blue background tint |

Colors are drawn from the logo's Pantone spot inks (Blue 072 C wordmark, 1235 C arc), matched to how the artwork renders on screen.

## Versioning

`@main` always serves the latest version. To pin to a stable release in production HTML, use a tag instead: `@v1.0`.

## License

Brand assets are property of Apex Paramedics. Use only for Apex Paramedics and partner-related materials.
