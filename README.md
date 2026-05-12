# KAazi Solutions — Website

Marketing site for KAazi Solutions, served at **kaazidevs.com**.

## Stack

Single-page static site. No build step.

- HTML + Tailwind CSS (via CDN)
- Vanilla JS for scroll reveal and mobile menu
- Inter font (Google Fonts)

## Local preview

Open `index.html` directly in a browser, or run a static server:

```bash
npx serve .
```

## Deployment

`CNAME` is configured for `kaazidevs.com`. To deploy:

1. Point DNS for `kaazidevs.com` at the chosen host (GitHub Pages, Vercel, Netlify, etc.)
2. Enable hosting on that platform
3. Verify HTTPS

The contact form currently shows a success message client-side only — wire up a backend (Formspree, Resend, custom endpoint) before launch.
