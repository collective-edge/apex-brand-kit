# Pushing this kit

The repo exists at `collective-edge/apex-brand-kit` and is public, which jsDelivr requires. The kit is checked out at `~/collective-edge/apex-brand-kit` with `origin` already set. Nothing here creates a repo.

Every `@main` CDN URL in the house points at the file you are about to publish. Run step 1 first, every time.

## Step 1. Verify before you push

```bash
cd ~/collective-edge/apex-brand-kit
python3 scripts/check-sync.py
python3 scripts/validate.py snippets/header-band.html templates/document.html templates/deck.html Examples/apex-one-pager.html
```

`check-sync.py` asserts three things and exits non-zero on any of them:

| Check | What it catches |
|---|---|
| Seven shared files byte-identical to `collective-edge-brand-kit` | A forked type layer. `reference/type-system.md`, `NEW-BRAND.md`, `brands.json`, `snippets/type-system.css`, `snippets/type-tokens.json`, `scripts/validate.py`, `scripts/check-sync.py` |
| `snippets/palette.css` defines all 17 semantic variables | A component that renders in one brand and breaks in another |
| Every scale row in `snippets/type-tokens.json` matches the CSS | The JSON and the stylesheet drifting apart |

`validate.py` checks rules 1, 2, 5, 9, 10, 13 and 14 from `reference/type-system.md` against the HTML. Skip `Examples/*.before.html`: those files are deliberate violations kept for comparison.

Both must exit 0. If `check-sync.py` reports a shared file differs, fix it in `collective-edge-brand-kit` and copy it down. Never edit a shared file inside this kit.

## Step 2. Push

```bash
cd ~/collective-edge/apex-brand-kit
git add .
git commit -m "Describe what changed"
git push
```

Work lands on `main` before the CDN serves it. The current branch is `type-system-v1`; open a pull request or merge it forward.

## Step 3. Confirm the CDN

Give jsDelivr 30–60 seconds to cache a first request, then hit the two files that every deliverable loads:

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/snippets/palette.css
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-color.svg
```

`snippets/type-system.css` is served from `collective-edge-brand-kit`, not from here. The type layer belongs to the parent brand.

## Step 4. Tag a release

Tag once the kit is stable so production materials can pin a fixed version.

```bash
git tag v1.0
git push --tags
```

Replace `@main` with `@v1.1` in CDN URLs to pin. Bump the minor version for additive changes, the major version when a value in section 3, 4 or 5 of `reference/type-system.md` changes.

## Installing the kit on a machine

```bash
git clone https://github.com/collective-edge/apex-brand-kit ~/.claude/skills/apex-brand-guidelines
```

## Registering the kit with CE-General

Point `agent_roles/general-agent.md` in `collective-edge/general-agent` at this kit’s raw `SKILL.md`, under **Brand kits**:

```
https://raw.githubusercontent.com/collective-edge/apex-brand-kit/main/SKILL.md
```

Role-md changes need a new worker image. Merging to `master` auto-deploys to acceptance. Production is the manual `deploy.yml`.

## Re-exporting the logos

The shipping SVGs under `assets/logos/` are production art, supplied as SVG. The vector master is `assets/logos/source/apex-paramedics-PMS123-PMS072.eps`. For a re-export, open the EPS in Illustrator, `File → Export → SVG`, and overwrite under the same names. `brands.json` maps every logo role to its file, so add a role there rather than inventing a filename.
