# KAazi Solutions — Website

Marketing site for KAazi Solutions, served at **kaazidevs.com** via GitHub Pages.

## Stack

Static HTML with a single Tailwind CSS build step.

- HTML in `index.html`
- Tailwind utilities compiled from `src/input.css` → `styles.css` (committed, served by Pages)
- Vanilla JS for scroll reveal, mobile menu, FAQ accordion, service modals, hero counters
- Inter font (Google Fonts)
- Custom CSS for animations and brand tokens lives inline in `<style>` inside `index.html`

## Workflow

Install once after cloning:

```bash
npm install
```

Whenever you add or remove a Tailwind utility class in `index.html`, rebuild:

```bash
npm run build
```

That regenerates `styles.css`. **Commit both `index.html` and `styles.css`** together.

For active development, run watch mode in a separate terminal:

```bash
npm run watch
```

It rebuilds on every save.

## Local preview

After building, open `index.html` directly in a browser, or run a static server:

```bash
npx serve .
```

## Brand tokens

Brand colors live in `:root` CSS variables at the top of the `<style>` block in `index.html`:

```css
--brand-orange:    #f97316;
--brand-pink:      #ec4899;
--brand-purple:    #8b5cf6;
--brand-gradient:  linear-gradient(135deg, ...);
```

Change those four to rebrand the site. The Tailwind utility classes (`from-orange-500 via-pink-500 to-purple-600`) scattered throughout the HTML still hardcode the same hexes — those would need a find-and-replace if doing a full rebrand.

## Deployment

The repo deploys automatically to **kaazidevs.com** via GitHub Pages on every push to `main`.

DNS at Namecheap:
- Apex A records → GitHub Pages IPs (185.199.108–111.153)
- `www` CNAME → `kaazi-devs.github.io`
- MX, SPF, DKIM, DMARC → Microsoft 365 (sales@kaazidevs.com mailbox)

Contact form submits to Formsubmit via a hashed token URL — the email is not exposed in the HTML source.
