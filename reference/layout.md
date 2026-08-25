# Apex Paramedics · house layout

Blue is the structure. Gold is the spark.

Every block below is copy-pasteable. Load `type-system.css` then `palette.css` first. Style through the `.bk-*` classes and the `--fg-*` / `--bg-*` / `--border-*` variables. A raw `--apex-*` value appears only where the brand color is the point: the band ground, the accent rule, a chart series.

Every type value here comes from the scale in `reference/type-system.md`. Do not substitute a near-equivalent.

---

## What changed at v1.0

| Element | Was | Now |
|---|---|---|
| Band title | 800, `+1.5px` | 700 on dark, `0.030em` |
| Uppercase caps labels | 800 | 600 |
| Table header row | 800, 9pt | 600, 9pt |
| Flowchart node text | 800 | 600 on dark |
| Stat numeral | 800, 36pt to 60pt | 700, 42pt |
| Unit label | 500 | 400 |
| Footer | 400, 8pt | 400, 9pt |
| All tracking | px | em |
| Field separator | `\|` | `·` |
| Decision node | pill, `border-radius: 999px` | rectangle at 6px, like every other node |

Weight 500 is not in the ladder. Anything that was 500 becomes 400.

The decision pill is gone because role is now communicated by fill, never by shape. A pre-v1.0 Apex flowchart still carrying 999px decision nodes is out of date, not wrong to have existed. Re-cut it to 6px. `999px` survives for pills only, in section 8.

---

## 1. Header band

Full-width strip across the top of the page. Blue Deep ground, 3px gold rule along the bottom edge echoing the arc, white horizontal logo at the right.

`.bk-on-dark` drops the display weight from 800 to 700 and adds 0.005em tracking. Do not set the weight by hand.

```html
<header class="bk-on-dark" style="background:var(--bg-band); border-bottom:3px solid var(--border-band-rule);
        padding:0.32in 0.5in; display:flex; align-items:center; justify-content:space-between; gap:24px;">
  <div class="bk-display-md bk-caps" style="max-width:none; margin:0;">Field operations brief</div>
  <img src="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg"
       alt="Apex Paramedics" style="width:1.6in; height:auto; display:block; flex:0 0 auto;">
</header>
```

| Property | Value |
|---|---|
| Ground | `--bg-band` `#1D225E` |
| Bottom rule | 3px `--border-band-rule` `#FDB61C` |
| Title | `.bk-display-md.bk-caps`, 42pt print, 56px web, weight 700, tracking 0.030em, leading 1.10 |
| Logo | `horizontal-on-dark`, 1.4in to 1.8in wide. 1.6in is the default. Never below 110px or 1in |
| Padding | 0.32in vertical, 0.5in horizontal |

`.bk-caps` works at every step in the ladder. Each step declares its own `--tr-caps` and one rule applies it, so `.bk-h1.bk-caps` opens to +0.030em, `.bk-h4.bk-caps` to +0.060em and `.bk-body.bk-caps` to +0.070em. Rule 7 puts uppercase on a title, band or divider surface and on labels, and sentence case on headings inside a document. The band is a title surface, so the title takes `bk-caps`.

For a one-pager, swap `.bk-display-md` for `.bk-h1` and keep `bk-caps`: 30pt print, 40px web, weight 600 on dark, tracking 0.035em, leading 1.18.

`max-width: none` on the title is deliberate. The band is a flex row bounded by the logo, so `--measure-display` 16ch would cut the line short of the width the band actually gives it. Everywhere outside the band the measure holds.

An optional gradient runs `#1D225E` to `#2B338D` left to right. Keep the left end solid so the title holds contrast:

```css
style="background:linear-gradient(90deg, var(--apex-blue-deep) 0%, var(--apex-blue-deep) 55%, var(--apex-blue) 100%);"
```

---

## 2. Sub-banner

Thin Apex Blue strip directly under the header band. Carries a kicker, a partner name or a category. Never more than four words.

```html
<div class="bk-on-dark" style="background:var(--apex-blue); padding:8px 0.5in;">
  <div class="bk-eyebrow" style="margin:0; color:var(--fg-on-dark-1);">Ground transport · Alameda County</div>
</div>
```

| Property | Value |
|---|---|
| Ground | `--apex-blue` `#2B338D` |
| Text | `.bk-eyebrow`, 9pt print, 12px web, weight 600, uppercase, tracking 0.085em, the 0.080em step plus the rule 4 bonus this dark strip carries |
| Color | `--fg-on-dark-1` `#FFFFFF`. Override the default `--fg-on-dark-3`, which is too dim on this ground |
| Padding | 8px vertical, 0.5in horizontal |
| Separator | `·`, never a pipe |

---

## 3. Flowchart nodes

Every node is a rectangle at `--radius-md` 6px. Role is communicated by fill, never by shape. Node and branch labels are weight 600 uppercase through `.bk-caps`, which resolves to 0.085em on a dark fill and 0.080em on white. Never hand-set the case or the tracking: a hand-set value drops the rule 4 bonus.

```html
<div style="display:flex; align-items:center; gap:16px; flex-wrap:wrap;">

  <!-- Standard step -->
  <div class="bk-on-dark" style="background:var(--diagram-process); border:1px solid var(--diagram-process-border);
       border-radius:var(--radius-md); padding:12px 16px; min-width:160px;">
    <div class="bk-body-sm bk-caps" style="margin:0; text-wrap:pretty; max-width:var(--measure-body);
         color:var(--fg-on-dark-1); font-weight:600;">Dispatch received</div>
    <div class="bk-caption" style="margin:4px 0 0; text-wrap:pretty; max-width:var(--measure-caption);
         color:var(--fg-on-dark-2);">Within 60 seconds</div>
  </div>

  <!-- Action / highlight step -->
  <div class="bk-on-dark" style="background:var(--apex-blue); border:1px solid var(--apex-blue-deep);
       border-radius:var(--radius-md); padding:12px 16px; min-width:160px;">
    <div class="bk-body-sm bk-caps" style="margin:0; text-wrap:pretty; max-width:var(--measure-body);
         color:var(--fg-on-dark-1); font-weight:600;">Crew assigned</div>
  </div>

  <!-- Decision -->
  <div class="bk-on-dark" style="background:var(--diagram-decision); border:1px solid var(--diagram-decision-border);
       border-radius:var(--radius-md); padding:12px 16px; min-width:160px;">
    <div class="bk-body-sm bk-caps" style="margin:0; text-wrap:pretty; max-width:var(--measure-body);
         color:var(--fg-on-dark-1); font-weight:600;">ALS required</div>
  </div>

  <!-- Warning / critical -->
  <div class="bk-on-dark" style="background:var(--diagram-warning); border:1px solid var(--diagram-warning-border);
       border-radius:var(--radius-md); padding:12px 16px; min-width:160px;">
    <div class="bk-body-sm bk-caps" style="margin:0; text-wrap:pretty; max-width:var(--measure-body);
         color:var(--fg-on-dark-1); font-weight:600;">Divert active</div>
  </div>

  <!-- Branch label · the border carries the branch color, the text does not.
       #4a8e3a on #FFFFFF measures 4.02:1 and fails 4.5:1 at 9pt. -->
  <div style="background:var(--bg-canvas); border:1px solid var(--diagram-decision);
       border-radius:var(--radius-sm); padding:2px 8px;">
    <span class="bk-caption bk-caps" style="margin:0; text-wrap:pretty; max-width:var(--measure-caption);
          color:var(--fg-1); font-weight:600;">Yes</span>
  </div>

</div>
```

| Role | Fill | Border |
|---|---|---|
| Standard step | `--diagram-process` `#3e3e3e` | `#2a2a2a` |
| Action / highlight | `--apex-blue` `#2B338D` | `#1D225E` |
| Decision | `--diagram-decision` `#4a8e3a` | `#3a7029` |
| Warning / critical | `--diagram-warning` `#f57c00` | `#cc6600` |
| Branch label | `--bg-canvas` `#FFFFFF`, text `--fg-1` `#1E293B` | matches the branch outcome |

Connectors are `--diagram-connector` `#3e3e3e` at 1.8pt, with arrow markers. Diagram role colors are identical in every brand kit. Never invent a hue for a role.

Gold never appears as a node fill. Gold is a brand accent, not a status color.

A node caption is `--fg-on-dark-2` `#D6DAEC`, which measures 7.69:1 on `#3e3e3e`. The inherited `--fg-on-dark-3` `#9EA5C4` measures 4.40:1 there and fails 4.5:1.

White node text measures 10.70:1 on `#3e3e3e` and 10.71:1 on `#2B338D`, and both clear. It measures 4.02:1 on `#4a8e3a` and 2.70:1 on `#f57c00`, and both fail 4.5:1. Those two fills and their white text are inherited from the pre-v1.0 kits and are frozen pending a decision from the brand owner. Do not recolor them here. Until that decision lands, a Decision or Warning node carries a short label only, and every fact it signals also appears in the running text or the table beside the diagram.

---

## 4. Stat callout

Numerals are 700, not 800. At 42pt and up, ExtraBold reads as a slab rather than a number. Every numeral carries `tabular-nums`, which `.bk-stat` sets.

The kicker is `.bk-body-sm.bk-caps` at weight 600, not `.bk-eyebrow`. Section 4 of the type standard sets a caps label at the size of the body it labels, and the unit label under the numeral is `.bk-body-sm`.

```html
<div style="display:flex; gap:48px; flex-wrap:wrap;">

  <div style="border-top:2px solid var(--apex-gold); padding-top:8px;">
    <div class="bk-body-sm bk-caps" style="font-weight:var(--weight-semibold);">Median response</div>
    <div class="bk-stat" style="color:var(--fg-accent);">8.4</div>
    <div class="bk-body-sm" style="margin:4px 0 0; text-wrap:pretty; max-width:var(--measure-body);">minutes, county average</div>
  </div>

  <div style="border-top:2px solid var(--apex-gold); padding-top:8px;">
    <div class="bk-body-sm bk-caps" style="font-weight:var(--weight-semibold);">Transports</div>
    <div class="bk-stat" style="color:var(--fg-accent);">14,207</div>
    <div class="bk-body-sm" style="margin:4px 0 0; text-wrap:pretty; max-width:var(--measure-body);">calendar year 2025</div>
  </div>

</div>
```

| Part | Value |
|---|---|
| Kicker | `.bk-body-sm.bk-caps`, 10.5pt print, weight 600, uppercase, tracking 0.080em, `--fg-2` `#64748B` |
| Gold mark | 2px `--apex-gold` `#FDB61C` rule above the group. `#B77808` measures 3.68:1 and clears nothing below the `.bk-h3` step, so gold marks the callout and never sets the label |
| Numeral | `.bk-stat`, 42pt print, 56px web, weight 700, tracking -0.015em, `--fg-accent` `#2B338D` |
| Unit label | `.bk-body-sm`, 10.5pt print, weight 400, `--fg-2` `#64748B` |

On a dark ground, wrap the group in `.bk-on-dark` and set the numeral to `--apex-gold` `#FDB61C`. The kicker becomes `--fg-on-dark-3`.

Bright gold `#FDB61C` is never the numeral color on white. Use `--fg-accent` there.

---

## 5. Tables

Header row is 600 uppercase at 9pt, never 800. `.bk-table` sets `tabular-nums` on every cell so digits align down the column.

Set the 10.5pt step once on the cell rule. `.bk-body-sm` on a `td` also drags in `max-width: var(--measure-body)` 54ch, and a body measure on a table cell fights the table layout algorithm for column widths it has no business influencing.

```html
<style>
  .run-table td {
    padding: 8px 12px;
    border-bottom: 1px solid var(--border-1);
    font-size: var(--fs-body-sm);
    line-height: var(--lh-body-sm);
    letter-spacing: calc(var(--tr-body-sm) + var(--tr-dark, 0em));
    font-weight: var(--weight-regular);
    color: var(--fg-1);
  }
  .run-table td.num { text-align: right; white-space: nowrap; }
</style>

<table class="bk-table run-table" style="width:100%; border-collapse:collapse;">
  <thead>
    <tr class="bk-on-dark" style="background:var(--apex-blue-deep);">
      <th style="padding:8px 12px; color:var(--fg-on-dark-1);">Unit</th>
      <th style="padding:8px 12px; color:var(--fg-on-dark-1);">Shift</th>
      <th style="padding:8px 12px; color:var(--fg-on-dark-1); text-align:right;">Runs</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background:var(--bg-canvas);">
      <td><span class="bk-code">M-114</span></td>
      <td>0700 to 1900</td>
      <td class="num">12</td>
    </tr>
    <tr style="background:var(--bg-surface);">
      <td><span class="bk-code">M-207</span></td>
      <td>1900 to 0700</td>
      <td class="num">9</td>
    </tr>
  </tbody>
</table>
```

| Part | Value |
|---|---|
| Header fill | `--apex-blue-deep` `#1D225E` |
| Header text | `.bk-table th`, 9pt, weight 600, uppercase, tracking 0.085em, the 0.080em step plus the rule 4 bonus this dark row carries, `--fg-on-dark-1` |
| Body rows | `--bg-canvas` `#FFFFFF`, alternating with `--bg-surface` `#f3f3fb` |
| Body text | `.run-table td`, 10.5pt, leading 1.55, tracking 0.005em, weight 400, `--fg-1` `#1E293B` |
| Why `--fg-1` | `--fg-2` `#64748B` measures 4.31:1 on the `#f3f3fb` row and fails 4.5:1. Primary data is always `--fg-1` |
| Borders | `--border-1` `#E2E8F0` hairline |
| Cell padding | 8px vertical, 12px horizontal |

Unit IDs, run numbers and authorization numbers go in `.bk-code`. Montserrat’s capital I, lowercase l and figure 1 are three identical stems.

Alternate rows only when alternation helps a reader track a long row. Never for decoration.

---

## 6. Footer

Slim full-width strip. Hairline top border, or a 2px gold rule for a branded finish.

```html
<footer style="border-top:1px solid var(--border-1); padding:8px 0.5in;
        display:flex; justify-content:space-between; align-items:baseline; gap:24px;">
  <span class="bk-caption bk-measure-none" style="margin:0;">Apex Paramedics · Field operations brief</span>
  <span class="bk-caption bk-measure-none" style="margin:0; font-weight:700;
        color:var(--fg-accent);">Rev.&nbsp;<span class="bk-code">08.26</span></span>
</footer>
```

| Part | Value |
|---|---|
| Top border | 1px `--border-1` `#E2E8F0`, or 2px `--apex-gold` `#FDB61C` |
| Left text | `.bk-caption`, 9pt, weight 400, `--fg-3` `#64748B` |
| Right marker | `.bk-caption` at weight 700, `--fg-accent` `#2B338D`, value in `.bk-code` |
| Separator | `·` between brand and document title |
| Padding | 8px vertical, 0.5in horizontal |

`.bk-measure-none` on both spans. `.bk-caption` carries `--measure-caption` 40ch, and the footer rail is bounded by the page, not by a measure. A brand string that wrapped to a second row would drop the revision value out of baseline alignment. Tracking is not hand-set either: `.bk-caption` supplies `--tr-caption`. Restating the value by hand freezes the footer the day the token moves.

The revision marker takes a non-breaking space, and the value itself goes in `.bk-code`: `Rev.&nbsp;<span class="bk-code">08.26</span>`. Nothing in the footer drops below 9pt.

---

## 7. Powered by Collective Edge

Apex Paramedics is an operating company under Collective Edge. Where an Apex surface is doing something a reader might wonder about, the lockup says who built it. It is a signal, not a legal footnote.

The rule, and it is the whole rule: **the CE lockup rides beside the Apex brand, never inside it, so a hairline keeps the two marks distinct.** The two read as two brands rather than one combined mark. Nothing is merged, nested or recolored to match the other side.

The CSS is shared and identical in every kit: [`snippets/cobrand.css`](../snippets/cobrand.css). Load it after the palette.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/snippets/cobrand.css">
```

**Dark ground.** The Apex band `--bg-band` `#1D225E`. This is the shipped case, the one running in the Apex website footer and the internal dashboard sidebar.

```html
<div class="bk-on-dark" style="background:var(--bg-band); padding:32px 0.5in;">
  <img src="https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-white.svg"
       alt="Apex Paramedics" style="width:158px; height:auto; display:block;">
  <div class="ce-powered">
    <span>Powered by</span>
    <img src="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/assets/logos/horizontal-white.svg"
         alt="CE · Collective Edge" width="204" height="34">
  </div>
</div>
```

**Light ground.** The white canvas `--bg-canvas` `#FFFFFF`, for a one-pager or report footer. Same geometry, black lockup, hairline in `--border-1`.

```html
<div class="ce-powered ce-powered-light">
  <span>Powered by</span>
  <img src="https://cdn.jsdelivr.net/gh/collective-edge/collective-edge-brand-kit@main/assets/logos/horizontal-black.svg"
       alt="CE · Collective Edge" width="204" height="34">
</div>
```

**Text only.** Where no lockup fits, `.ce-powered-text` sets the phrase at `.bk-eyebrow` values, 12px web and 9pt print at weight 600 with 0.080em tracking. The customer dashboard ships it at 9px and 700, which is under the 9pt floor and heavier than the caps-label step. Use the class.

```html
<p class="ce-powered-text">Powered by Collective Edge</p>
```

| Part | Value |
|---|---|
| Lockup width | 204px, rendering 34px tall on the 450 x 75 artwork |
| Label | `--fs-caption` 12px web and 9pt print, weight 600, `--tr-caps-small` 0.080em, uppercase |
| Label on dark | `--fg-on-dark-3` `#9EA5C4` on `#1D225E`, 5.98:1 |
| Label on light | `--fg-3` `#64748B` on `#FFFFFF`, 4.76:1 |
| Hairline on dark | 1px `--border-on-dark` `rgba(255,255,255,0.12)` |
| Hairline on light | 1px `--border-1` `#E2E8F0` |
| Spacing | 24px above the hairline and 24px below it, 12px between label and lockup |

204px is deliberate. It runs wider than the 158px Apex mark above it because it is sized to read at a glance rather than sit quietly in a corner. The 110px logo minimum in this kit is a floor, not a target.

The light lockup goes on `--bg-canvas`, not on `--apex-surface` `#f3f3fb`. The same grey measures 4.31:1 on the tint, under the 4.5:1 small-text threshold.

**Where it belongs.** The footer of any Apex site or printed document. The sidebar header of any Apex dashboard. The closing slide of a deck. The foot of a report. A data page or a methodology page. Anywhere a number was computed rather than typed.

**Where it does not.** On the Apex mark itself or inside the Apex lockup. On a clinical instruction. On a patient-facing consent or safety document. Twice on one surface. Set as type where the mark fits.

---

## 8. Page rules

| Rule | Value |
|---|---|
| Body measure | `max-width: 54ch`, which `.bk-body` already sets. Never let body text run a wide container |
| Vertical rhythm | Every vertical value is a multiple of 4 |
| Heading spacing | Space above a heading is three times the space below it. Defaults are 48px above, 16px below |
| Alignment | Flush left, ragged right. Never justified |
| Heading case | Sentence case inside a document. Uppercase on a title, band or divider surface, and for labels. Always tracked, never past four words |
| Print | `orphans: 3; widows: 3`. Tables and figures set `break-inside: avoid` |
| Radius | 6px for nodes and cards, 2px for chips, 999px only for pills |
| Elevation | The house is flat. Shadow signals elevation, never decoration |
