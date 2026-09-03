# KAazi Solutions — Website

Marketing site for KAazi Solutions, served at **kaazidevs.com** via GitHub Pages.

Positioning: *Compute for AI. From the rack to the agent.* — AI infrastructure, platform, and services.

## Stack

Single static page. Nearly all styling is hand-written CSS in the inline `<style>` block of `index.html`; the Tailwind build exists but emits only a small reset plus a handful of utilities.

- HTML, CSS and JS all in `index.html`
- Design tokens in `:root` at the top of that `<style>` block
- Tailwind reset/utilities compiled from `src/input.css` → `styles.css` (committed, served by Pages)
- Vanilla JS only: live status-bar date, footer year, nav scroll shadow, mobile menu, contact-form AJAX submit
- FAQ uses native `<details>` / `<summary>` — no JS
- Fonts: Inter (body) + JetBrains Mono (data, labels, status bar), both from Google Fonts

## Brand tokens

Defined in `:root` inside `index.html`:

```css
--bg:      #0B0C0F;   /* page background          */
--text:    #EDECE6;   /* primary text             */
--accent:  #E66A55;   /* coral, used sparingly    */
```

Direction is dark-first, monospace for data, sans for prose. **No serif, no gold, no gradients on backgrounds.**

## Content rules

The site must not claim infrastructure that is not operational. Specifically, avoid:

- "active" / "live" / "operational" / "available now" region or cluster wording
- specific GPU counts, uptime percentages, MW capacity, or latency figures
- customer logos

Regions are presented as a **roadmap** — United States, Nigeria, Southern Africa — with availability "announced as capacity becomes operational."

## Workflow

Install once after cloning:

```bash
npm install
```

If you add or remove a Tailwind utility class in `index.html`, rebuild and commit both files:

```bash
npm run build
```

## Preview

Don't open `index.html` over `file://` — the CSP behaves differently there and fonts load differently, so it misrepresents the real page. Push to `main` and check **kaazidevs.com** once the Pages build finishes (~40s).

## Social preview image

`images/og-image.svg` is the source; `images/og-image.png` (1200×630) is what the meta tags reference, because LinkedIn, X, Facebook and Slack do not render SVG previews. **After editing the SVG, regenerate the PNG** — any headless-Chromium screenshot at 1200×630 with the SVG inlined into a blank page works, e.g.:

```bash
msedge --headless=new --window-size=1200,630 --screenshot=og-image.png wrapper.html
```

## Deployment

Deploys automatically to **kaazidevs.com** via GitHub Pages on every push to `main`. `main` is protected (PR + 1 approval, admin bypass).

DNS at Namecheap:
- Apex A records → GitHub Pages IPs (185.199.108–111.153)
- `www` CNAME → `kaazi-devs.github.io` (still resolves correctly after the repo moved to `Dev-Gashap`)
- MX, SPF, DKIM, DMARC → Microsoft 365 (sales@kaazidevs.com mailbox)

Contact form submits to Formsubmit via a hashed token URL — the email is not exposed in the HTML source.

## Known open items

- DMARC is still `p=none`; tighten to `p=quarantine; pct=25`, then `pct=100`, then `p=reject`
- Footer social links are `href="#"` placeholders — need real LinkedIn / X / GitHub URLs or removal
- Team photos for Timothy Oke and Afeez Adeyemo are still mono initials
