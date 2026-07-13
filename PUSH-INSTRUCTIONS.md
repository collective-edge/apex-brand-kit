# How to push this to GitHub (one-time, ~3 minutes)

Everything is already prepared in this folder. You just need to create the repo and push.

## Step 1. Create the empty repo on GitHub

Go to **https://github.com/organizations/collective-edge/repositories/new** and create:

- **Repository name:** `apex-brand-kit`
- **Visibility:** **Public** (required for the jsDelivr CDN to work)
- **Do NOT** initialize with a README, .gitignore, or license — this folder already has them.

Click **Create repository**.

## Step 2. Push from terminal

```bash
cd "/Users/jacob/Desktop/Apex Brand Kit/apex-brand-kit"
git init
git add .
git commit -m "Initial Apex Paramedics brand kit"
git branch -M main
git remote add origin https://github.com/collective-edge/apex-brand-kit.git
git push -u origin main
```

Or, with the GitHub CLI already authenticated, one line does it all:

```bash
cd "/Users/jacob/Desktop/Apex Brand Kit/apex-brand-kit" && git init && git add . && git commit -m "Initial Apex Paramedics brand kit" && git branch -M main && gh repo create collective-edge/apex-brand-kit --public --source=. --remote=origin --push
```

## Step 3. Verify the CDN is live

After pushing, hit this URL in a browser (give jsDelivr 30–60 seconds to cache the first time):

```
https://cdn.jsdelivr.net/gh/collective-edge/apex-brand-kit@main/assets/logos/horizontal-color.svg
```

You should see the Apex logo. The font, colors.json, and CSS are all at the same base URL.

## Step 4. (Optional) Re-export logos at full fidelity

The SVG logos included here (`horizontal-color.svg`, `horizontal-white.svg`, `mark-color.svg`, `mark-white.svg`) were traced from the Apex artwork and are production-usable. If you want a pixel-perfect re-export from the original vector art, open `assets/logos/source/apex-paramedics.eps` in Illustrator, `File → Export → SVG`, and overwrite the files (keep the same names — `SKILL.md` already points at them). Make a white-wordmark variant for `horizontal-white.svg`.

## Step 5. Register the kit with CE-General

Add a short pointer under the **Brand kits** section of `collective-edge/general-agent`'s `agent_roles/general-agent.md`, pointing at this kit's raw `SKILL.md`:

```
https://raw.githubusercontent.com/collective-edge/apex-brand-kit/main/SKILL.md
```

(Same pattern as the Royal entry. Role-md changes need a new worker image: merge to `master` auto-deploys to acceptance; prod is the manual `deploy.yml`.)

## Step 6. Tell teammates

Share this single line. They run it once and Claude on their machine applies the brand automatically forever:

```bash
git clone https://github.com/collective-edge/apex-brand-kit ~/.claude/skills/apex-brand-guidelines
```

## Updating later

Edit any file, then:

```bash
cd "/Users/jacob/Desktop/Apex Brand Kit/apex-brand-kit"
git add . && git commit -m "Describe what changed" && git push
```

Changes go live on the CDN within a minute or two.

## Versioning (optional, for production safety)

Once stable, tag a release so production materials can pin to a fixed version:

```bash
git tag v1.0
git push --tags
```

Then in CDN URLs, replace `@main` with `@v1.0`.
