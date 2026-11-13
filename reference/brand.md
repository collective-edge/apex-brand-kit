# Apex Paramedics · brand reference

The full tables behind `SKILL.md`: color, logo, co-brand and voice. Type is in `reference/type-system.md`. Layout is in `reference/layout.md`. Chart color is in `reference/data-color.md`.

Apex Paramedics is an operating company under Collective Edge. Its colors are navy and gold, drawn from its own mark.

Collective Edge, Apex Paramedics and Royal Ambulance share one standard. The sections, the order and the rules in this file are the same in all three kits. Color, logo and brand facts differ.

`snippets/palette.css` is authoritative for color and `tokens.json` mirrors it. If this file disagrees with either, this file is stale.

---

## 1. Color

### 1.1 Palette

Blue is the structure. Gold is the spark. Blue carries bands and headings. Gold is one rule or one mark on a surface, never a field. Text and rules come from the shared neutrals in 1.3.

| Name | Token | Hex | RGB | Use |
|---|---|---|---|---|
| Apex Blue Deep | `--apex-blue-deep` | `#1D225E` | 29, 34, 94 | The band, as `--bg-band` and `--bg-inverse`. Hero grounds, footers, table header rows |
| Apex Blue | `--apex-blue` | `#2B338D` | 43, 51, 141 | Primary. Headings, links, buttons, accent bars. Accent text, as `--fg-accent`. A filled block, as `--bg-mid`. Pantone Blue 072 C |
| Apex Blue Light | `--apex-blue-light` | `#9699C7` | 150, 153, 199 | Thin rules and hover states. Never text. Never a large background |
| Apex Gold | `--apex-gold` | `#FDB61C` | 253, 182, 28 | The 2.25pt (3px) rule under the band, as `--border-band-rule`. Kicker marks. Numerals and caps labels on a dark ground. Pantone 1235 C. Never text on white |
| Apex Gold Deep | `--apex-gold-deep` | `#B77808` | 183, 120, 8 | Gold text on white, at 18pt in print or 24px on screen and up |
| Surface Tint | `--apex-surface` | `#f3f3fb` | 243, 243, 251 | Callout fill, as `--bg-surface` |
| White | `--apex-white` | `#FFFFFF` | 255, 255, 255 | The page. Text on a dark ground |

The palette is drawn from the mark. The wordmark is Pantone Blue 072 C and the arc is Pantone 1235 C. Three more `--apex-*` names resolve to the shared neutrals in 1.3: `--apex-charcoal` `#23232A`, `--apex-muted` `#6D6D77` and `--apex-hairline` `#E4E4E9`. `--apex-black` is `#000000`.

### 1.2 Grounds

Every brand has the same six grounds, from lightest to darkest. White is the page. The last column lists the only text that sits on each ground.

| Ground | Token | Hex | RGB | Against white | Text on it |
|---|---|---|---|---|---|
| Canvas | `--bg-canvas` | `#FFFFFF` | 255, 255, 255 | | `--fg-1`, `--fg-2`, `--fg-3`, `--fg-accent` |
| Surface | `--bg-surface` | `#f3f3fb` | 243, 243, 251 | 1.10:1 | `--fg-1`, `--fg-2`, `--fg-3`, `--fg-accent` |
| Surface 2 | `--bg-surface-2` | `#E5EAFF` | 229, 234, 255 | 1.20:1 | `--fg-1`, `--fg-2`, `--fg-accent`. Never `--fg-3` |
| Mid | `--bg-mid` | `#2B338D` | 43, 51, 141 | | `--fg-on-dark-1`, `--fg-on-dark-2`. Never `--fg-on-dark-3` |
| Band | `--bg-band` | `#1D225E` | 29, 34, 94 | | `--fg-on-dark-1`, `--fg-on-dark-2`, `--fg-on-dark-3` |
| Hero | `--bg-inverse` | `#1D225E` | 29, 34, 94 | | `--fg-on-dark-1`, `--fg-on-dark-2`, `--fg-on-dark-3` |

Apex runs Hero and Band on one ground, `#1D225E`. Mid is Apex Blue. Surface 2 `#E5EAFF` is step 100 of the blue ramp.

### 1.3 Neutrals

One neutral family sets text and rules in all three brands. It leans neither blue nor purple, so it sits beside every brand color. Ratios are on `#FFFFFF`.

| Name | Token | Hex | RGB | On white | Use |
|---|---|---|---|---|---|
| Ink | `--neutral-ink` | `#23232A` | 35, 35, 42 | 15.61:1 | Body text and headings on light |
| Secondary | `--neutral-secondary` | `#565860` | 86, 88, 96 | 7.09:1 | Secondary text |
| Tertiary | `--neutral-tertiary` | `#6D6D77` | 109, 109, 119 | 5.12:1 | Captions and metadata. The dimmest text |
| Dimmed | `--neutral-dimmed` | `#8A8B93` | 138, 139, 147 | 3.39:1 | Marks only. Never text |
| Border | `--neutral-border` | `#D0D0D6` | 208, 208, 214 | 1.54:1 | Borders and table rules. Never text |
| Hairline | `--neutral-hairline` | `#E4E4E9` | 228, 228, 233 | 1.27:1 | Hairlines and dividers. Never text |
| Tint 2 | `--neutral-tint-2` | `#E5E6EA` | 229, 230, 234 | 1.25:1 | Stronger neutral tint |
| Tint | `--neutral-tint` | `#F0F1F4` | 240, 241, 244 | 1.13:1 | Neutral surface tint |
| Mid | `--neutral-mid` | `#4E4F58` | 78, 79, 88 | 8.13:1 | Mid tone fill. Diagram process nodes and connectors |
| On-dark body | `--neutral-on-dark-body` | `#DDDDE3` | 221, 221, 227 | | Body text on a dark ground |
| On-dark caption | `--neutral-on-dark-caption` | `#A3A4AC` | 163, 164, 172 | | Captions on a dark ground |

### 1.4 Semantic layer

Style through these names. They are identical in every brand, so a component built for one brand renders correctly in another with only `palette.css` swapped. `tokens.json` carries the same names under `foreground`, `background` and `border`.

| Token | Hex | Use |
|---|---|---|
| `--fg-1` | `#23232A` | Primary text on light |
| `--fg-2` | `#565860` | Secondary text |
| `--fg-3` | `#6D6D77` | Tertiary text, metadata, captions. The dimmest text |
| `--fg-4` | `#8A8B93` | Dimmed marks. Never text |
| `--fg-accent` | `#2B338D` | Brand-colored text. Apex Blue. 10.71:1 on white |
| `--fg-on-dark-1` | `#FFFFFF` | Headings and primary text on a dark ground |
| `--fg-on-dark-2` | `#DDDDE3` | Body text on a dark ground |
| `--fg-on-dark-3` | `#A3A4AC` | Captions and labels on a dark ground |
| `--bg-canvas` | `#FFFFFF` | The page |
| `--bg-surface` | `#f3f3fb` | Callouts |
| `--bg-surface-2` | `#E5EAFF` | The stronger tint |
| `--bg-elevated` | `#FFFFFF` | Raised surface |
| `--bg-mid` | `#2B338D` | Filled block |
| `--bg-band` | `#1D225E` | Header band |
| `--bg-inverse` | `#1D225E` | Hero, title slide |
| `--border-1` | `#E4E4E9` | Hairlines and dividers |
| `--border-2` | `#D0D0D6` | Stronger rule |
| `--border-on-dark` | `rgba(255,255,255,0.12)` | Rules on a dark ground |
| `--border-band-rule` | `#FDB61C` | The 2.25pt (3px) gold rule under the band. 8.24:1 on the band |

The focus ring on a control is `#23232A` on light and `#FFFFFF` on dark, 2px wide at a 2px offset.

### 1.5 Alerts

Four meanings, one family, identical in every brand, so a signal never changes meaning between documents. Green means good and nothing else. A brand color is never a status color. A word or an icon always travels with the color.

| Meaning | Base | Text | Tint | Text on tint | On dark |
|---|---|---|---|---|---|
| Go · cleared, on time, in service, favorable | `#1E7A4D` | `#1E7A4D` | `#DAF8DF` | `#1E7A4D` | `#56B580` |
| Warn · at risk, pending, watch, caution | `#B5821A` | `#926603` | `#FFEFDD` | `#926603` | `#E9B457` |
| Stop · failed, out of service, blocked, unfavorable | `#B0322B` | `#B0322B` | `#FDE9E6` | `#B0322B` | `#EB685C` |
| Info · neutral notice | `#2A5A8C` | `#2A5A8C` | `#E3F0FF` | `#2A5A8C` | `#5796D9` |

| Step | CSS name | `tokens.json` | Use |
|---|---|---|---|
| Base | `--alert-<name>` | `alert.<name>.base` | A fill, a rule or a dot on a light ground |
| Text | `--alert-<name>-text` | `alert.<name>.text` | Text on white and on Surface |
| Tint | `--alert-<name>-tint` | `alert.<name>.tint` | A pill or a callout fill |
| Text on tint | `--alert-<name>-on-tint` | `alert.<name>.onTint` | Text on the matching tint |
| On dark | `--alert-<name>-on-dark` | `alert.<name>.onDark` | Text, dots and rules on a dark ground |

Worst measured ratio across white, the three brand surfaces and the three brand bands:

| Step | Go | Warn | Stop | Info |
|---|---|---|---|---|
| Text on white and on Surface | 4.71:1 | 4.51:1 | 5.57:1 | 6.33:1 |
| Text on tint | 4.68:1 | 4.52:1 | 5.39:1 | 6.18:1 |
| On dark, on the bands | 5.76:1 | 7.72:1 | 4.62:1 | 4.69:1 |

**Canonical names and aliases.** `--alert-*` is canonical. It holds one value on every ground. Pick the step for the ground. Three sets are aliases of it and resolve to the same values:

| Alias | Resolves to | Note |
|---|---|---|
| `--status-go`, `--status-warn`, `--status-stop`, `--status-info` | The alert base | Under `.bk-on-dark` they move to the on-dark step |
| `--dir-favorable`, `--dir-unfavorable`, `--dir-caution` | Go text, stop text, warn text | The data layer. `--dir-neutral` is Tertiary `#6D6D77` |
| `--diagram-decision`, `--diagram-warning` | Go base, warn base | Section 1.6 |

**Status on a dark ground.** Status works on a band. Use the on-dark step: `#56B580`, `#E9B457`, `#EB685C`, `#5796D9`. The worst case is stop on the Apex band, 4.62:1.

**Warn.** The base `#B5821A` measures 3.40:1 on white. It is a fill, a rule or a dot, never text. Warn text is `#926603`, 5.09:1 on white. Text on an amber fill is `#23232A`, 4.59:1. White on amber measures 3.40:1 and fails.

**Surface 2.** On Surface 2, go text measures 4.45:1 and warn text 4.25:1. Neither sits bare on that ground. Carry them in a tint pill there. Stop and info hold.

### 1.6 Diagram roles

Identical in every brand, so a diagram reads the same in any document. Every node is a rectangle with a 6px radius. Fill carries the role, never shape. Each role names the one text color that clears contrast on its fill.

| Role | Fill | Border | Text | Contrast | Use |
|---|---|---|---|---|---|
| Decision | `#1E7A4D` | `#036139` | `#FFFFFF` | 5.32:1 | Decision boxes, questions, branch points |
| Warning | `#B5821A` | `#926603` | `#23232A` | 4.59:1 | Warnings, advisories. Ink, never white |
| Process | `#4E4F58` | `#23232A` | `#FFFFFF` | 8.13:1 | Neutral process steps, context boxes |
| Connector | `#4E4F58` stroke | | | | Lines between nodes, 1.8pt, with arrow markers |
| Brand role | None | | | | This kit adds no role |

A node carries its own ground, so these values do not change on a band.

### 1.7 Charts

Chart colors come from the house data set, never from the brand palette. A brand color is never a chart series. The standard is [data-color.md](data-color.md). The one chart value that follows the brand is the sequential ramp:

| Step | 100 | 200 | 300 | 400 | 500 | 600 | 700 |
|---|---|---|---|---|---|---|---|
| On light | `#E5EAFF` | `#C2CFFE` | `#A0B1F1` | `#8193DE` | `#6374C9` | `#4452B1` | `#2B338D` |
| On dark | `#20285A` | `#313C7A` | `#45539F` | `#5A6BC7` | `#7286EA` | `#95A8FA` | `#C2CFFF` |

The Apex ramp is blue and step 700 is `--fg-accent` `#2B338D`. Steps 100 and 200 are for continuous scales only. On a dark ground the lightest step is the largest value.

### 1.8 Contrast

WCAG 2 relative luminance. Body-size text needs 4.5:1. Large text needs 3:1 and starts at 18pt regular or 14pt bold. Use these figures. Do not restate a different one.

| Pair | Ratio | Verdict |
|---|---|---|
| `#23232A` on `#FFFFFF` | 15.61:1 | Any size |
| `#23232A` on `#f3f3fb` | 14.14:1 | Any size |
| `#23232A` on `#E5EAFF` | 13.04:1 | Any size |
| `#565860` on `#FFFFFF` | 7.09:1 | Any size |
| `#565860` on `#f3f3fb` | 6.43:1 | Any size |
| `#565860` on `#E5EAFF` | 5.93:1 | Any size |
| `#6D6D77` on `#FFFFFF` | 5.12:1 | Any size. The dimmest text |
| `#6D6D77` on `#f3f3fb` | 4.64:1 | Any size |
| `#6D6D77` on `#E5EAFF` | 4.27:1 | Fails. Never on Surface 2 |
| `#8A8B93` on `#FFFFFF` | 3.39:1 | Never text |
| `#2B338D` on `#FFFFFF` | 10.71:1 | Any size |
| `#2B338D` on `#f3f3fb` | 9.70:1 | Any size |
| `#2B338D` on `#E5EAFF` | 8.95:1 | Any size |
| `#B77808` on `#FFFFFF` | 3.68:1 | 18pt and up only |
| `#B77808` on `#f3f3fb` | 3.34:1 | 18pt and up only |
| `#9699C7` on `#FFFFFF` | 2.74:1 | Never text |
| `#FDB61C` on `#FFFFFF` | 1.77:1 | Never text |
| `#FDB61C` on `#1D225E` | 8.24:1 | Any size |
| `#FDB61C` on `#2B338D` | 6.06:1 | Any size |
| `#FFFFFF` on `#1D225E` | 14.56:1 | Any size |
| `#DDDDE3` on `#1D225E` | 10.76:1 | Any size |
| `#A3A4AC` on `#1D225E` | 5.87:1 | Any size |
| `#FFFFFF` on `#2B338D` | 10.71:1 | Any size |
| `#DDDDE3` on `#2B338D` | 7.92:1 | Any size |
| `#A3A4AC` on `#2B338D` | 4.32:1 | Fails. Never on Mid |

### 1.9 Never

- `#8A8B93`, `#D0D0D6` and `#E4E4E9` are never text.
- A brand color is never a status color and never a chart series.
- A status color is never a theme, a background or a decoration.
- The band is never the reading surface of a document.
- No color enters a document that is not in `tokens.json`.
- `#FDB61C` is never text on white, never a large background and never the fill of a panel that carries body text.
- `#B77808` is never below 18pt in print or 24px on screen. Never an eyebrow, a caption, a table cell or running text.
- `#9699C7` is never text, never a large background and never a table header fill.
- `#2B338D` is never the color of long-form body text.
- `#f3f3fb` never carries white text.
- Dark grounds are `#1D225E` and `#2B338D` only.

---

## 2. Logo

### 2.1 Roles and files

Ask for a role, never a filename. Filenames differ between brands. `-on-light` is the file placed on a light background. `-on-dark` is the file placed on a dark one. SVG files are in `assets/logos/`. PNG files are in `for-humans/logos/png/`, each at two widths.

| Role | SVG | PNG | The artwork |
|---|---|---|---|
| `horizontal-on-light` | `horizontal-color.svg` | `Apex-Paramedics-horizontal-blue-1200w.png`, `-2400w.png` | `#2B338D` APEX PARAMEDICS under the `#FDB61C` arc |
| `horizontal-on-dark` | `horizontal-white.svg` | `Apex-Paramedics-horizontal-white-1200w.png`, `-2400w.png` | White APEX PARAMEDICS under the `#FDB61C` arc |
| `compact-on-light` | `compact-on-light.svg` | `Apex-Paramedics-compact-blue-1200w.png`, `-2400w.png` | `#2B338D` APEX under the `#FDB61C` arc |
| `compact-on-dark` | `compact-on-dark.svg` | `Apex-Paramedics-compact-white-1200w.png`, `-2400w.png` | White APEX under the `#FDB61C` arc |
| `mark-on-light` | `mark-on-light.svg` | `Apex-Paramedics-mark-blue-512w.png`, `-1024w.png` | The `#2B338D` A with the `#FDB61C` arc through it |
| `mark-on-dark` | `mark-on-dark.svg` | `Apex-Paramedics-mark-white-512w.png`, `-1024w.png` | The white A with the `#FDB61C` arc through it |
| `stacked-on-light` | None | None | Apex ships no stacked lockup |
| `stacked-on-dark` | None | None | Apex ships no stacked lockup |
| `app-icon` | `app-icon.svg` | `Apex-Paramedics-app-icon-512w.png`, `-1024w.png` | The white A and the `#FDB61C` arc on a `#1D225E` square |

The horizontal lockup is the primary logo. The compact lockup is for small places, decks and corners. The mark is for avatars, badges and any space too small for the compact lockup. The app icon is for favicons and app tiles. The gold arc never appears on its own, at any size. `horizontal-on-light.svg` and `horizontal-on-dark.svg` in `assets/logos/` are byte-identical copies of `horizontal-color.svg` and `horizontal-white.svg`.

### 2.2 Specifications

| Property | Value |
|---|---|
| Horizontal viewBox | `0 0 687.72 289.25`, 2.378:1 |
| Compact viewBox | `0 0 682.3 240.66`, 2.835:1 |
| Mark viewBox | `0 0 300 299.36` |
| Stacked viewBox | None |
| App icon viewBox | `0 0 300 300` |
| Fill on light | `#2B338D` letters. `#FDB61C` arc |
| Fill on dark | `#FFFFFF` letters. `#FDB61C` arc |
| Minimum, horizontal | 110px on screen, 1in in print |
| Minimum, compact | 80px on screen, 0.75in in print |
| Minimum, mark | 16px on screen. No print value is stated |
| Minimum, app icon | 16px on screen. No print value is stated |
| Clear space | The height of the gold arc, on all four sides |
| Vector master | `assets/logos/source/apex-paramedics-PMS123-PMS072.eps`. The SVG files are converted from it |
| Embedding | Place the PNG in an office document. Reference the CDN URL with `<img>` in HTML. Never inline a copied SVG path |

### 2.3 Do not

- Do not stretch, skew or rotate a logo.
- Do not recolor a logo, and do not invert one with a filter. Pick the file for the ground.
- Do not add a shadow, a glow, an outline or a gradient.
- Do not place a logo on a photograph without a solid backing.
- Do not set a logo below its minimum size.
- Do not crop the clear space. Shrink the logo instead, down to the minimum.
- Do not put one brand’s logo twice on a page or slide.
- Do not show the gold arc on its own. The arc alone is not an Apex logo.
- Do not separate the wordmark from the arc, or the A from the arc in the mark.
- Do not render the arc in blue or the wordmark in gold.
- Do not use the compact lockup where the horizontal one fits.

---

## 3. Co-brand

Apex Paramedics and Royal Ambulance are operating companies under Collective Edge, and the reader should be able to see it. The rules in this section are identical in all three kits.

### 3.1 The lockup

“Powered by Collective Edge” is one lockup. It is the label `POWERED BY` over the Collective Edge horizontal lockup, under a hairline. `cobrand` in `brands.json` carries every value below, and `snippets/cobrand.css` is the HTML implementation.

| Part | Value |
|---|---|
| Label | `POWERED BY`. Weight 600, uppercase, 9pt in print and 12px on screen, tracking 0.080em |
| Label color | `#6D6D77` on white, 5.12:1. `#A3A4AC` on a dark ground |
| Lockup on white | The Collective Edge `horizontal-on-light` file, `assets/logos/horizontal-black.svg` in the Collective Edge kit |
| Lockup on a dark ground | The Collective Edge `horizontal-on-dark` file, `assets/logos/horizontal-white.svg` in the Collective Edge kit |
| Width | 2.125in (204px) wide, 0.354in (34px) tall. The artwork is 6:1 |
| Floor | 120px. A floor, not a target |
| Hairline | 0.75pt (1px) above the label. `#E4E4E9` on white. White at 12 percent on a dark ground |
| Spacing | On a site: 18pt (24px) above the hairline, 18pt (24px) between hairline and label, 9pt (12px) between label and lockup. In a document: `reference/layout.md` section 3.12 |
| Ground | The light lockup sits on white, not on a tint |
| CSS classes | `.ce-powered` on a dark ground. `.ce-powered ce-powered-light` on white. `.ce-powered-text` where no mark fits |

The label measures 5.87:1 on this brand’s band.

### 3.2 Where it goes

1. “Powered by Collective Edge” appears once on every Apex Paramedics and Royal Ambulance document.
2. A Collective Edge document carries the Collective Edge logo in its band and no lockup.
3. Where the Collective Edge mark shares a surface with another brand, the lockup is on that surface, once.

| Surface | Place |
|---|---|
| Memo, one-pager | The footer row, at left |
| Report | The last block of the body on the last page |
| Deck | The closing slide |
| Site | The footer |
| Dashboard | The sidebar header |
| Data page or methodology page | Anywhere a number was computed and not typed |

### 3.3 Never

- Never put the lockup on the partner’s own mark or inside its lockup.
- Never merge, nest or recolor either mark to match the other.
- Never use it twice in one document or on one surface.
- Never set the phrase as type where the mark fits.
- Never design the lockup down to the 120px floor.
- Never put it on a clinical instruction.
- Never put it on a patient-facing consent or safety document.

The last two are the only documents that carry no lockup.

### 3.4 Who leads

Ask whose name is on the door.

| | Partner led | Collective Edge led |
|---|---|---|
| When | The surface belongs to Apex Paramedics, Royal Ambulance or another partner. The default | A Collective Edge product delivered to a partner or its customer |
| Logo | The partner’s logo heads the surface | The Collective Edge logo heads the surface |
| Palette | The partner’s palette runs the band and the accents | White canvas and the Collective Edge tiers |
| Collective Edge adds | Type, hairlines and whitespace. No hue. The lockup, once | The partner’s color as the one hue, on live and active states only. Never a chart series |

When in doubt, the partner leads. Hold one mode on a surface. Never stack more than three marks in one lockup. Take a partner’s hex from `brands.json` or from that partner’s kit, never from a copy. `unreconciled` in `brands.json` lists placeholder colors for brands with no kit. Confirm those with the owner before use.

### 3.5 The wedge

The Edge wedge is the one part of the Collective Edge block mark that takes color, and that color is the partner’s. Every combination ships as a file in the Collective Edge kit, under `assets/logos/`. Never recolor a mark by hand.

| Wedge | Hex | On light | On dark |
|---|---|---|---|
| Alone | `#C8C8C8` | `mark-black.svg` | `mark-white.svg` |
| With Royal Ambulance | `#572E72` | `mark-black-royal.svg` | `mark-white-royal.svg` |
| With Apex Paramedics | `#FDB61C` | `mark-black-apex.svg` | `mark-white-apex.svg` |

The wedge color never leaves the wedge. The block and the letters stay black or white on every surface. On an Apex surface the wedge is Apex Gold `#FDB61C`.

---

## 4. Voice

### 4.1 Character

Short. Specific. About the work. Apex speaks the way a field crew speaks.

### 4.2 Rules

- Short declarative sentences. Active verbs. No filler and no throat-clearing.
- No em dashes. Use a period, a comma or `·`. An en dash only in a date or number range, per rule 14 of the type system.
- Exact values. The real number, never a rounded one. The hex, never a description of the color.
- A label, a value, and nothing between them. No helper text under a field, no caption restating the thing above it, no parenthetical after a heading.
- Write a caption only when it carries information the thing above it does not.
- Sentence case for every heading. Uppercase for the band title, the title slide title and the lockup label only. Always tracked, never past four words.
- No emoji, no exclamation points, no rhetorical questions.
- Clinical and operational terms stay precise. Never soften a protocol term.
- Name people, partners and facilities exactly as they write themselves.
- When you hand work back, state the brand, the document type, the logo role and how the font embedded.
- Write about the work. If structure, position or a rendered example can carry the information, carry it that way.

---

## 5. Only in this kit

### 5.1 The gold rule

The Apex band carries a 2.25pt (3px) `#FDB61C` rule along its lower edge. It is `--border-band-rule`. Gold on `#1D225E` measures 8.24:1.

### 5.2 The delivered artwork

The delivered files carried `#000F9F` and `#FFB71B`. Both are normalised to `#2B338D` and `#FDB61C`, so the house ships one blue and one gold. The delivered originals are in the git history. In the mark the arc is cut square at the left and right edges of the box. That is the drawing, not a cropping error. The arc-only files `mark-color.svg` and `mark-white.svg` are deleted, and `scripts/validate.py` fails on any reference to them as check L1.

### 5.3 Raster fallback

Where only the color raster is reachable on a `#1D225E` ground, place it on a white chip: `#FFFFFF` fill, 2px radius, clear space held on all four sides. Never knock the logo out and never filter it. The same chip is the fix for a photographic ground.

---

## 6. Files and versions

| What | Path |
|---|---|
| CDN root | `https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/` |
| Repository | `collective-edge/apex-brand-kit` |
| Palette, authoritative | `snippets/palette.css` |
| Colors as data | `tokens.json`, version 2.0 |
| Type as data | `snippets/type-tokens.json` |
| Registry of every brand | `brands.json` |
| Logos | `assets/logos/` as SVG, `for-humans/logos/png/` as PNG |
| Fonts | `for-humans/fonts/static/` as static files. The variable font is served from the Collective Edge kit |
| Templates | `templates/` |

`@main` serves the latest. Production pins a tag in place of `@main`. Bump the minor version for an additive change. Bump the major version when a palette value or a mark changes.

These files predate the house type system. They stay on the CDN because documents already point at them. New work never loads them.

| Deprecated | Replaced by |
|---|---|
| `snippets/brand-base.css` | `snippets/type-system.css` and `snippets/palette.css` |
| `assets/colors.json` | `tokens.json` |
| `assets/fonts/Montserrat-VariableFont_wght.ttf` in this kit | The Collective Edge copy, woff2 first, TTF second |
